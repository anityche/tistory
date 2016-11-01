
### 윈도우, 지킬, 깃헙

일전에 깃헙에 블로그를 편하게 만들 수 있다는 방법이 있어서 테스트 하다가 이해력이 부족해서 환경설정 문서만 보는데서 그쳤었다.
짬이 난 김에 마무리까지 한 번 해보려고 기록을 남긴다.

> 윈도우 10 64비트를 기준으로 작성한다. 
> github 계정이 있다는 전제조건 하에 진행한다.

#### Ruby 설치 및 설정

- [ruby(2.x 버전이 안정적이라고 한다), rubydevkit을 다운로드](http://rubyinstaller.org/downloads/archives)
- ruby 설치(설치시 체크 항목이 3개 있는데, *path* 자동등록은 꼭 해주도록 하자)
- `cmd` 커맨드 모드에서 devkit 설치 폴더로 이동
    - `ruby dk.rb init` 명령어 실행 
    - `ruby dk.rb install` 명령어 실행 


#### Bundler 설치 및 설정

ruby의 package manager 라고 한다. ruby를 설치 했다면 `gem` 명령어로 이어서 설치를 진행.

```
C:\RubyDevKit>gem install bundler

ERROR:  Could not find a valid gem 'bundler' (>= 0), here is why:
          Unable to download data from https://rubygems.org/ - SSL_connect returned=1 errno=0 state=SSLv3 read server certificate B: certificate verify failed (https://api.rubygems.org/specs.4.8.gz)
```

##### Error - gem install bundler 

설치시 오류가 발생했다. 자격이 없다고 하는건가?

- [ssl-certificate update guides](http://guides.rubygems.org/ssl-certificate-update/)

친절하다. 가이드 페이지 방문했더니 루비잼을 업데이트 하란다.

> 해당 글 작성일 기준으로 가이드에서는 gem 버전이 2.6.7 이었고 최신은 [2.6.8](https://rubygems.org/gems/rubygems-update-2.6.8.gem) 이었다.

기왕이면 최신 버전이 좋겠다 싶어서 최신으로 GEM을 다운받았다. 

- [최신 잼 다운로드](https://rubygems.org/pages/download) 

> 잼설치폴더 파악 명령어 `gem which rubygems`

음... 가이드 페이지에서는 뭐 지우고 다시 설치하라는 둥 뭐라뭐라 하라는 듯 한데 그냥 잼 다운로드 페이지에 업데이트 안내가 
되어 있길래 그대로 따라했다.

그리고 1.2 이하의 버전과 초과의 버전으로 명령어가 나누어 지는 듯 한데 어쨋든 영어 난독증이라, 나타난 3가지 명령어를 다 실행해봐도...

```
C:\Ruby22-x64>gem update --system

ERROR:  While executing gem ... (Gem::RemoteFetcher::FetchError)
    SSL_connect returned=1 errno=0 state=SSLv3 read server certificate B: certificate verify failed (https://api.rubygems.org/specs.4.8.gz)

C:\Ruby22-x64>gem install rubygems-update

ERROR:  Could not find a valid gem 'rubygems-update' (>= 0), here is why:
          Unable to download data from https://rubygems.org/ - SSL_connect returned=1 errno=0 state=SSLv3 read server certificate B: certificate verify failed (https://api.rubygems.org/specs.4.8.gz)

C:\Ruby22-x64>update_rubygems

'update_rubygems'은(는) 내부 또는 외부 명령, 실행할 수 있는 프로그램, 또는
배치 파일이 아닙니다.
```

...거지같다.
음... 받은 gem이 있는 위치로 이동해서 다시 실행.

```
C:\Ruby22-x64\lib\ruby\2.2.0\rubygems\ssl_certs>gem install rubygems-update

Successfully installed rubygems-update-2.6.8
...(생략)
WARNING:  Unable to pull data from 'https://rubygems.org/': SSL_connect returned=1 errno=0 state=SSLv3 read server certificate B: certificate verify failed (https://api.rubygems.org/specs.4.8.gz)
1 gem installed
```

후후. 그리고 다시 bundler 설치 진행.

그런데 똑같은 오류!!! 아.. 어쩐지 위에 **WARNING** 문구가 마음 한 켠에 걸리더라!!!

그래서 다시 가이드 페이지로 직행.

- [MANUAL SOLUTION TO SSL ISSUE](http://guides.rubygems.org/ssl-certificate-update/#manual-solution-to-ssl-issue)

내용인즉, 새로운 암호화 권한 파일을 바꿔치기 해라. 정도인 것 같다. 다시 밝히지만 영어 난독증이라..

1. `\Ruby22-x64\lib\ruby\2.2.0\rubygems\ssl_certs` 폴더로 이동
1. AddTrustExternalCARoot.pem 파일을 열어서 내용을 [GlobalSignRootCA.pem](https://raw.githubusercontent.com/rubygems/rubygems/master/lib/rubygems/ssl_certs/index.rubygems.org/GlobalSignRootCA.pem) 파일의 내용과 바꿔치기

> GlobalSignRootCA.pem 파일의 내용은 작성일자 기준 내용이므로 직접 다운로드 받거나 내용을 확인하시길


그리고 나서 다시 bundler 설치... 이번에는 되겠지...

```
c:\Ruby22-x64>gem install bundler

Fetching: bundler-1.13.6.gem (100%)
...(생략)
Done installing documentation for bundler after 17 seconds
1 gem installed
```

후후.


#### Python 설치

과정을 최소화 하기 위해 Python 설치 관련 과정은 패스하려고 했으나 

```
c:\Ruby22-x64>gem update
Updating installed gems
Updating bigdecimal
Fetching: bigdecimal-1.2.7.gem (100%)
ERROR:  Error installing bigdecimal:
        The 'bigdecimal' native gem requires installed build tools.

Please update your PATH to include build tools or download the DevKit
from 'http://rubyinstaller.org/downloads' and follow the instructions
at 'http://github.com/oneclick/rubyinstaller/wiki/Development-Kit'
Updating io-console
Fetching: io-console-0.4.6.gem (100%)
ERROR:  Error installing io-console:
        The 'io-console' native gem requires installed build tools.

Please update your PATH to include build tools or download the DevKit
from 'http://rubyinstaller.org/downloads' and follow the instructions
at 'http://github.com/oneclick/rubyinstaller/wiki/Development-Kit'
Updating json
Fetching: json-2.0.2.gem (100%)
ERROR:  Error installing json:
        The 'json' native gem requires installed build tools.

Please update your PATH to include build tools or download the DevKit
from 'http://rubyinstaller.org/downloads' and follow the instructions
at 'http://github.com/oneclick/rubyinstaller/wiki/Development-Kit'
Updating minitest
Fetching: minitest-5.9.1.gem (100%)
Successfully installed minitest-5.9.1
Parsing documentation for minitest-5.9.1
Installing ri documentation for minitest-5.9.1
Installing darkfish documentation for minitest-5.9.1
Done installing documentation for minitest after 3 seconds
Parsing documentation for minitest-5.9.1
Done installing documentation for minitest after 0 seconds
Updating power_assert
Fetching: power_assert-0.3.1.gem (100%)
Successfully installed power_assert-0.3.1
Parsing documentation for power_assert-0.3.1
Installing ri documentation for power_assert-0.3.1
Installing darkfish documentation for power_assert-0.3.1
Done installing documentation for power_assert after 0 seconds
Parsing documentation for power_assert-0.3.1
Done installing documentation for power_assert after 0 seconds
Updating psych
Fetching: psych-2.1.1.gem (100%)
ERROR:  Error installing psych:
        The 'psych' native gem requires installed build tools.

Please update your PATH to include build tools or download the DevKit
from 'http://rubyinstaller.org/downloads' and follow the instructions
at 'http://github.com/oneclick/rubyinstaller/wiki/Development-Kit'
Updating rake
Fetching: rake-11.3.0.gem (100%)
rake's executable "rake" conflicts with C:/Ruby22-x64/bin/rake
Overwrite the executable? [yN]  y
Successfully installed rake-11.3.0
Parsing documentation for rake-11.3.0
Installing ri documentation for rake-11.3.0
Installing darkfish documentation for rake-11.3.0
Done installing documentation for rake after 3 seconds
Parsing documentation for rake-11.3.0
Done installing documentation for rake after 0 seconds
Updating rdoc
Fetching: rdoc-4.2.2.gem (100%)
rdoc's executable "rdoc" conflicts with C:/Ruby22-x64/bin/rdoc
Overwrite the executable? [yN]  y
rdoc's executable "ri" conflicts with C:/Ruby22-x64/bin/ri
Overwrite the executable? [yN]  y
Depending on your version of ruby, you may need to install ruby rdoc/ri data:

<= 1.8.6 : unsupported
 = 1.8.7 : gem install rdoc-data; rdoc-data --install
 = 1.9.1 : gem install rdoc-data; rdoc-data --install
>= 1.9.2 : nothing to do! Yay!
Successfully installed rdoc-4.2.2
Parsing documentation for rdoc-4.2.2
Installing ri documentation for rdoc-4.2.2
Installing darkfish documentation for rdoc-4.2.2
(eval):3: warning: string literal in condition
(eval):2: warning: string literal in condition
Done installing documentation for rdoc after 21 seconds
Parsing documentation for rdoc-4.2.2
Done installing documentation for rdoc after 6 seconds
Updating test-unit
Fetching: test-unit-3.2.1.gem (100%)
Successfully installed test-unit-3.2.1
Parsing documentation for test-unit-3.2.1
Installing ri documentation for test-unit-3.2.1
Installing darkfish documentation for test-unit-3.2.1
Done installing documentation for test-unit after 9 seconds
Parsing documentation for test-unit-3.2.1
Done installing documentation for test-unit after 1 seconds
Gems updated: bigdecimal io-console json minitest power_assert psych rake rdoc test-unit
```


#### Jekyll 설치 및 설정

- github에서 사용할 테마 선정([테마다운로드](http://jekyllthemes.org/))
- 다운로드 받은 압축파일을 자신이 사용할 github page site 명으로 수정 ([GitHub Pages](https://pages.github.com/))


- 참조블로그
    + [http://hochulshin.com/how-to-use-jekyll-on-github-1/](http://hochulshin.com/how-to-use-jekyll-on-github-1/)