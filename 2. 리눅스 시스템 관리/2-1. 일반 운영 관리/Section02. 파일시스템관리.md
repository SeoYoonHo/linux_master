### 소유권과 허가권
- ls -l 하면 나오는 파일 및 디렉터리 허가권
- [파일유형][소유자허가권][그룹허가권][다른사용자허가권]
- 허가권(권한) 변경 명령어는 chmod [option] mode file(s)
- 소유권 변경 명령어는 chown [options] owner:[:group] files(s)
- 그룹의 소유권 변경 chgrp -> 본인이 소유한 파일에 대해서는 본인이 속한 그룹내에서 소유권 변경가능
- 기본허가권 변경은 umask 사용해서 변경가능
- 기본에서 umask값을 뺸게 기본 권한인(파일:666, 디렉터리:777)
- 즉, umask가 002이면 파일은 666-002=664 이고, 디렉터리는 777-002=775 가 된다.

### 특수권한
- Set-UID 권한비트, Set-GID 권한비트, 스티키 비트 존재
  #### Set-UID 권한비트
    - 설정되면 사용자가 아니라 해당 파일의 소유자권한으로 실행됨(/usr/bin/passwd는 root가 소유자이기 떄문에 root권한으로 실행됨. -> rwsr-x-r-x)
    - 실행권한이 없는 파일에 설정하게되면 'S' --> 대문자 로 표시됨
    - 'chmod u+s file' or 'chmod u=srwx,g=r,o=r file' or 'chmod 4744 file'
  #### Set-GID 권한비트
    -  설정되면 파일의 그룹권한으로 실행됨
    - 'chmod g+S file' or 'chmod u=rwx,g=sr,o=r file' or 'chmod 2744 file'
  #### Sticky 비트
    - 디렉터리에만 적용 가능함
    - 모든 권한이 있지만 삭제는 파일의 소유자만 가능
    - 대표적으로 /tmp 폴더
    - 'chmod o+t directory' or 'chmod 1777 directory'

### 파일링크
- 이미 존재하는 파일에 대한 포인터
- 크게 하드링크와 심볼릭링크로 나누어짐
- 아이노드 : 파일이 사용하는 모든 블록을 가리키는 포인터들을 포함하는 하나의 블록
- 하드링크의 경우 해당 원본 파일의 아이노드를 가리킴
- 심볼릭링크의 경우 원파일의 아이노드의 경로를 가리킴 -> 새로운 아이노드가 생성이 됨. 해당 아노드는 원본파이르이 아이노드를 가리킴(바로가기 느낌)
- https://i5i5.tistory.com/341
  #### 하드링크
  - 동일한 파일시스템 내에서만 하드링크 생성가능
  - 디렉터리 링크는 안됨
  - ln명령어를 통해 하드링크 생성 가능
  - ln source.file hardlink.file
  #### 소프트링크(심볼릭링크)
  - 서로 다른 파일시스템 위치 해도 괜찮
  - 디렉터리도 생성 가능
  - ln -s source.file softlink.file

### 디렉터리 관리
  #### pwd
  - 현재 파일 시스템상 어떤 디렉토리에 위치해있는지 출력(Working Directory)
  - 셸 내장 pwd와 bin에 위치한 외부명령어 존재(type pwd)
  
  #### cd
  - 작업 디렉터리 변경

  #### mkdir
  - 디렉터리 생성명령어
  - mkdir [option] directory
  - -m, --mode : 허가권 지정
  - -p, --parents : 생성시 상위 디렉토리도 생성 --> 존재하지 않으면 같이 생성

  #### rmdir
  - 디렉터리 삭제 명령어(비어있어야함, 비어있지 않아도 삭제하려면 옵션에 -r옵션)
  - rmdir [option] directory
  - -p : 가장 아래디렉터리부터 상위디렉터리로 거슬러 올라가면서 삭제. 비어있으면 삭제하고 비어있지 않으면 삭제 안함

### 파일 관리
  #### ls
  - 지정한 경로에 존재하는 파일과 디렉터리 리스트 출력
  - ls [option] file

  |옵션|설명|
  |----|---|
  |-a, --all|숨겨진 파일도 모두 출력|
  |-F, --classify|각 파일마다 파일의 유형도 같이 출력. @:심볼릭링크, *:실행파일, =:소켓, |:파이프 |
  |-ㅣ|파일 디렉터리 각각 한줄씩 자세한|
  |-d, --directory|디렉토리 자체를 표시, 디렉토리 이름만 나열하고, 그 안의 서브디렉토리나 파일목록은 출력안함. ls -d */|
  |-t|마지막 수정시간 기준 최신|
  |-u|-lt옵션과 사용, 접근시간 기준|
  |-i, --inode|각 파일의 아이노드 번호 출력|
  |-r, --reverse|정렬순서를 반대로|
  |-R, --recursive|디렉터리가 존재하면 그 안의 파일목록도|
  |-S|파일 크기 기준 정렬|
  |-1|그냥 한줄에 하나씩 출력 덜자세하게|

  #### cp
  - 파일이나 디렉터리 복사. 출력 결과를 확인하고싶은 -v 옵션 사용
  - 이미 존재하는 경우 기본적으론 덮어쓰기. 원치않으면 -i 옵션 사용
  - cp [option] source ... destination
  
  |옵션|설명|
  |----|---|
  |-r, -R, --recursive|디렉터리 내의 파일이나 디렉터리도 같이 복사|
  |-i, --interactive|덮어쓰기전에 확인먼저 받음|
  |-f, --force|덮어쓰기 안되면, 삭제하고 복사시도|
  |-b|덮어쓰기하지 않고 기존 파일뒤에 ~ 붙여 백업|
  |-s, --symbolic-link|복사 대신에 심볼릭링크 생성. 소스는 절대경로, 대상은 현재디렉토리 아니어야됨|
  |-p|권한이나 접근시간 수정시간 보존하여 복사|
  |-v, --verbose|항목의 정보를 상세히 출력|
  |-d|심볼릭 링크 자체를 복사|
  |-a, --archive|원본파일 정보 유지 복사  '-dR -preserve=ALL'과 동일|
  |-l, --link|하드링크 생성|
  |-u, --update|원본이 대상파일보다 최신또는 대상파일이 존재하지 않을떄 복사|

  #### rm
  - 지정한 파일을 삭제하는 명령어. 옵션 없으면 디렉터리는 지우지 않음. -r -R옵션 사용하면 가능
  - rm [option] file ...

  |옵션|설명|
  |----|---|
  |-i|삭제전 확인|
  |-f, --force|파일이 존재하지 않아도 무시|
  |-r, -R, --recursive|디렉터리와 그 이하 디렉터리 모두 삭제|
  - rm명령어는 실제 데이터를 지우는게 아님. 파일과 데이터간의 링크를 제거할 뿐
  - 만약 데이터까지 삭제하고싶으면 shred 명령어 사용 필요

  #### mv
  - 지정한 파일이나 디렉터리의 경로 수정이나 이름 변경 가능
  - mv [option] source ... destination

  #### touch
  - 파일의 파일스탬프 정보를 수정하는 명령어. 파일이 없는 경우 생성(디폴트는 현재시간)
  - touch [option] filename
  - 리눅스에서는 접근시간(access time), 수정시간(modification time), 변경 시간(change time)을 관리함
  - 변경시간이 더 넓은 개념 수정시간보다

  #### file
  - 파일의 유형을 확인하는 명령어
  - file [option] filename

  #### find
  - 파일시스템에 존재하는 파일과 디렉터리를 찾는 명령어
  - 많음....
  - find : 현재경로 밑의 모든 파일출력(디렉터리도)
  - find . /home : home 디렉터리와 현재디렉토리 밑의 모든 파일/디렉터리 출력
  - find . -name '*.zip'
  - find . -name 'apple' -type f
  - find . -group daemon
  - find . -user francis
  - find . -atime +5 : 접근시간이 5일 이상된, -5 이면 5일 이하인
  - find . -perm 754
  - find . -size -5G
  - find . -size +1G -exec mv '{}' ~/bigfiles \;
  - find . -name '*.log' -print0 | xargs -0 rm -f

### 텍스트 관련 명령어
  #### cat
  - 텍스트 파일의 내용 보거나, 다른파일로 복사, 기존 텍스트파일과 합치는 기능
  - cat [option] file

  #### head
  - 지정한 파일의 앞부분을 출력한다. 옵션 없으면 첫 10줄
  - head [option] file

  #### tail
  - 지정한 파일의 끝부분을 출력
  - tail [option] file

  #### more
  - 텍스트 한페이지씩
  - more [option] file

  #### less
  - 역시 한페이지씩 텍스트파일
  - 빠르고 더 좋음(한번에 메모리에 올리지 않음ㅈ)
  - less [option] file

  #### grep
  - 텍스트파일을 읽어서 지정한 패턴과 일치하는 문자열 출력
  - grep [option] pattern file

  #### wc
  - 지정한 파일에 대해 단어, 개행문자, 문자의 개수 등을 셀 수 있는 명령어
  - wc [option] file
  
  #### sort
  - 텍스트파일을 한줄씩 읽어서 정렬
  - sort [option] file
  - sort -k 3 person.txt : 3번찌 필드를 기준으로 정렬

  #### cut
  - 텍스트파일을 한 줄 또는 여러줄을 잘라낼 수 있는 명령어
  - cut [option] file

  #### split
  - 파일을 고정 크기의 여러 파일로 분할
  - split [option] file [file_name]

### 파일시스템 관리 및 복구
  - fdisk 파티션테이블 생성
  - mkfs 파일시스템으로 포맷팅
  - mount 마운팅

  #### fdisk
  - 디스크상에서 파이션을 생성,삭제,수정 명령어

  #### mkfs
  - 하드디스크를 사용할 수 있도록 파일 시스템을 생성하는 명령어
  - 내부적으로는 mke2fs 명령어 사용

  #### mount
  - 하드디스크 전체나 특정 파티션을 현재 존재하는 파일시스템의 디렉터리 구조에 붙여서 접근가능하게 하는 명령어