## 리눅스민트 설치 후 문제점 몇 가지 

사용환경 
- 한성노트북 u56 4757
- 리눅스민트 마테 17.3 로사 [하모니카][] 버전 

[하모니카]:http://hamonikr.org/ 

>하모니카 란, 한국어를 사용하는 사용자가 좋은 오픈소스 소프트웨어를 찾고 한국어 번역에 참여하고 발전시켜서 자유 라이선스에 따라서 이를 공개하도록 허용하고 권장하는 것입니다. 


### Intel Dual Band Wireless AC 3165

리눅스민트 설치 후 유선 랜카드는 문제가 없었는데 무선랜이 잡히지 않았다. 구글링 해보니 딱 나온다. 이전 버전 부터 같은 문제가 있는 듯.

다음과 같은 방법으로 Thank!! 라는 덧글을 많이 받은 듯.

```
wget https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-25.30.13.0.tgz
tar zxvf iwlwifi-7265-ucode-25.30.13.0.tgz
cd iwlwifi-7265-ucode-25.30.13.0
sudo cp iwlwifi-7265-13.ucode /lib/firmware/iwlwifi-3165-13.ucode
cd
sudo apt-get install build-essential linux-headers-generic
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz
tar zxvf backports-20151120.tar.gz
cd backports-20151120
make defconfig-wifi
make
sudo make install
```

참조사이트 
- [리눅스민트포럼](https://forums.linuxmint.com/viewtopic.php?f=53&t=210525)


### 서브라임텍스트 한글 먹통 

sublime text 설치 후 한글을 **fcitx** 로 사용하고 있는데 이것도 고질적인 문제인 듯 싶다.

특정 소스를 받아서 컴파일 후 사용하는 방법이 있는 듯 한데, 깊이 검색해볼 것 없이 **UIM-벼루**를 사용해서 해결했다. 
하지만 사용하다 보니 치명적인 단점이 있는데 마지막 글자가 정상적으로 출력이 되지 않고 *띄어쓰기*를 입력해야 비로소 입력이 끝난다. 
즉, 문장을 이어가는 중 개행(줄바꿈)을 하고 계속해서 입력시 띄어쓰기를 하지 않았다면 마지막 글자를 가지고 있다가 뿜어낸다...

개행 뿐만 아니고 글자가 틀려서 수정시 마찬가지로 띄어쓰기를 하지 않고 앞으로 이동하여 수정하려고 하면 마지막 글자를 뿜어낸다.

몇 번 계속해서 글자를 틀리고 수정하다 보면 저절로 마음의 소리가 튀어 나온다. 띠발! 하고...

>우리나라, 일본, 중국 3개 국가 언어의 공통적 문제로 보인다.


그래서 나도 중국 유저의 도움을 받기로 마음을 굳혔다. 내용은 깃헙에서 확인할 수 있다.

- github - [lyfeyaj](https://github.com/lyfeyaj/sublime-text-imfix) 

먼저, 원격저장소에서 로컬로 소스를 복사한다.

```
git clone https://github.com/lyfeyaj/sublime-text-imfix.git
```

복사한 위치로 이동 후 실행 명령어만 치면 끝!

```
cd sublime-text-imfix 
./sublime-imfix

--이하 출력내용 

Checking for installation of Sublime Text 3...........
/usr/bin/subl
.............................................Installed

Checking for installation of Fcitx Input Methods....
/usr/bin/fcitx
...........................................Installed
/usr/bin/subl
/usr/bin/fcitx

**************** Adding shared lib to sublime directory *****

**************** Checking for existing file *****************
[sudo] password for khan: 

**************** Replacing subl with new one ****************

**************** Sublime Text input method problem fixed! ****

**************** More: Installing extra skins ****************

**************** Un-packing skin into current folders ********

(생략)

** Copying skin to Fcitx skin folder: /usr/share/fcitx/skin **

Done!

Thanks for using this script to fix SublimeText 3 for Input Method.

Re-login your X windows and start to use SublimeText 3 with Fctix!


```


오류가 난다는 댓글이 있어서 **sublime-imfix** 실행 파일의 내용을 살펴봤다. 자세히는 모르겠고 서브라임텍스트와 fcitx 설치 여부를 
확인 하고 업데이트 하고 뭐 뭐 이런 저런 자동으로.

```
#!/bin/bash

echo "Checking for installation of Sublime Text 3..........."
if which subl
then
echo ".............................................Installed"
else
  echo "It seems that you do not install Sublime Text 3 in your system."
  echo 'Do you want to install it? [Y/N]'

  read sublime_input

  if [ $sublime_input == 'Y' ] || [ $sublime_input == 'y' ]
  then
    echo ''
    echo '**************** Adding Sublime Text 3 PPA *****************'
    echo ''
    sudo add-apt-repository -y ppa:webupd8team/sublime-text-3

    echo ''
    echo '**************** Updating and upgrading system **************'
    echo ''
    sudo apt-get update >> /dev/null && sudo apt-get upgrade >> /dev/null

    echo ''
    echo '**************** Installing Sublime Text 3 *****************'
    echo ''
    sudo apt-get install -y sublime-text-installer >> /dev/null

    echo ''
    echo '**************** Sublime Text 3 installed successfully *****'
  else
    echo ''
    echo '**************** Skip installing Sublime Text 3 ************'
  fi
fi

echo ''
echo "Checking for installation of Fcitx Input Methods...."

if which fcitx
then
  echo "...........................................Installed"
else
  echo "It seems that you do not install Fcitx Input Method in your system."
  echo 'Do you want to install it? [Y/N]'

  read fcitx_input

  if [ $fcitx_input == 'Y' ] || [ $fcitx_input == 'y' ]
  then
    echo ''
    echo '**************** Adding Fcitx PPA **************************'
    echo ''
    sudo add-apt-repository -y ppa:fcitx-team/nightly

    echo ''
    echo '**************** Updating system ***************************'
    echo ''
    sudo apt-get update >> /dev/null

    echo ''
    echo '**************** Installing Fcitx and Pinyin methods *******'
    echo ''
    sudo apt-get install -y fcitx fcitx-config-gtk fcitx-sunpinyin fcitx-googlepinyin fcitx-module-cloudpinyin fcitx-sogoupinyin > /dev/null

    echo ''
    echo '**************** Installing Fcitx related libs *************'
    echo ''
    sudo apt-get install -y build-essential libgtk2.0-dev >> /dev/null
    sudo apt-get install -y fcitx-table-all >> /dev/null

    echo ''
    echo '**************** Fcitx installed successfully! **************'
    echo ''
    echo '**************** Setting Fcitx as the default input method! *'
    im-switch -s fcitx -z default
  else
    echo ''
    echo '**************** Skip installing Sublime Text 3 ************'
  fi
fi

if which subl && which fcitx
then
  echo ''
  echo '**************** Adding shared lib to sublime directory *****'
  echo ''
  echo '**************** Checking for existing file *****************'
  if [ -e '/opt/sublime_text/libsublime-imfix.so' ]
    then
    echo ''
    echo '**************** libsublime-imfix.so is already existing ****'
  else
    sudo cp ./lib/libsublime-imfix.so /opt/sublime_text/
  fi

  echo ''
  echo '**************** Replacing subl with new one ****************'
  echo ''
  if [ -e '/usr/bin/subl' ]
    then
    sudo rm /usr/bin/subl && sudo cp ./src/subl /usr/bin/
  fi

  echo '**************** Sublime Text input method problem fixed! ****'
  echo ''
  echo '**************** More: Installing extra skins ****************'
  echo ''
  echo '**************** Un-packing skin into current folders ********'
  echo ''
  tar -zxvf src/anran.tar.gz

  echo '** Copying skin to Fcitx skin folder: /usr/share/fcitx/skin **'
  echo ''
  sudo cp -r anran /usr/share/fcitx/skin/
  rm -r anran

  echo 'Done!' 
  echo ''
  echo 'Thanks for using this script to fix SublimeText 3 for Input Method.'
  echo ''
  echo 'Re-login your X windows and start to use SublimeText 3 with Fctix!'
fi
```

마지막 `echo` 메세지의 오타가 눈에 보였다. **Fctix!** 라고...

아무튼.


하지만 제어센터에서 다시 fcitx 로 언어입력기를 선택하고 재 로그인을 해도 한글은 입력이 되지 않았다. 심지어 날 비웃기라도 하는 듯 
fcitx 설정을 보기 위해 우클릭을 하는 순간!

![Imgur](http://i.imgur.com/dNNu57a.png)

하... 결국, 치명적인 단점이 있음에도 해결책을 찾지 못해서 다시 UIM 으로 돌아왔다.
