# Shell Commands

### [1. Manual](#manual)

### [2. Navigating file system](#navigating-file-system)

### [3. Create & manage files](#create--manage-files)

### [4. Work with environment variables](#work-with-environment-variables)

### [5. Bonus](#bonus)

---

Unix에는 많은 shell들이 있다 대표적으로

- Bourne shell
- Bash
- fish
- zsh

## Manual

```sh
man          # 사용자 매뉴얼,  이 명령어가 뭔지 모르겠을 때 or 어떤 옵션들과 함께 쓸 수 있는지 알고싶을 때 사용
man man      # 매뉴얼에 대한 매뉴얼
clear        # 터미널의 모든 텍스트를 깔끔하게 청소
man clear    # 클리어에 대한 설명과 옵션을 볼 수 있다
```

## Navigating file system

```bash
pwd           #  지금 내가 어떤 경로에 있는지 확인 | Print Working Directory
              #  서버에서 로그를 남기거나 스크립트를 작성할 때 많이 사용

ls            # 현재 디렉토리 안에 있는 폴더와 파일을 볼 수 있다 (list)

ls 경로
ls 현재있는-폴더-안에있는-폴더명    # 특정한 폴더 / 경로 안에 있는 내용들을 보고 싶을 때

ls -l          # 파일에 대해 좀 더 자세한 내용들을 보여준다 (long)
ls -a          # UI로 볼 수 없는 숨겨진 파일이나 디렉토리를 보여준다 (all)
ls -la         # l, a를 함께 묶어서 옵션을 줄 수도 있다
open .         # 현재 경로를 파일 탐색기에서 열기
```

### cd command ( change direcory )

현재 있는 경로의 위치를 변경할 때 사용

```bash
cd 폴더명            # 폴더명(현재있는 경로에 존재하는 폴더의 이름)으로 이동
cd ..              # 상위 폴더로 이동
cd ~               # 현재 설정된 사용자의 홈 디렉토리(최상위 경로)로 이동
cd -               # 여기로 오기 전의 경로로 이동 | 두 경로를 왔다갔다 할 때 유용
```

### find

파일 시스템에서 특정한 파일이나 디렉토리를 찾을 때 유용하게 사용  
내가 현재 있는 경로와 그 하위에 있는 모든 폴더에 한해서 모든 텍스트 파일을 찾고 싶다면?

예시 1

```bash
find . -type file -name "*.txt"
# 현재 경로에서부터 시작해서, 타입은 파일, 이름은 모든 파일(*)인데 확장자가 txt로 끝나는 것을 찾는다
```

예시 2

```bash
find . -type directory -name "*2"
# 현재 경로부터 디렉토리 타입의 이름은 2로 끝나는 모든 폴더를 찾는다
```

### which

내가 지금 실행하고자 하는 프로그램이 어디에 설치 ・ 설정되어 있는지 경로를 확인할 때 사용

```bash
which node           # node의 실행경로를 확인
which code           # vscode의 경로를 확인
```

## Create & manage files

#### touch

```bash
touch 파일명.확장자      # 새로운 파일 생성
man touch             # 로 확인해보면 파일이 존재하지 않으면 파일을 생성
                      # 파일이 존재하면 파일의 수정한 날짜가 touch한 시점으로 업데이트
```

#### cat

```bash
cat file.text file_2.text  # cat 다음 파일 하나를 작성해도 되고 여러개 작성해도 된다
                           # (모든) 파일의 컨텐츠를 한번에 확인할 수 있다
```

#### echo

```bash
echo "string"                     # string을 터미널에 출력할 수 있다 (like echo 메아리..)
echo "Hello world" > file.text    # file.text을 만들면서 컨텐츠로 Hello World라는 문자가 들어감

# echo 문자열 > 파일   | 이렇게 화살표 괄호가 1개면 문자열대로 덮어씌우는 기능을 함 (이전에 있던 내용은 사라짐)

echo "adding text" >> file.text   # 꺽쇠괄호가 2개 이면 기존 컨텐츠에 문자열을 추가한다
```

#### mkdir

```bash
# make directory
mkdir 디렉토리명

mkdir -p 폴더명1/폴더명2/폴더명3    # 폴더명1 안에 폴더명2를 만들고 그 안에 또 폴더명3 디렉토리를 만듦
```

#### cp

```bash
# copy
cp file.text dir1/         # file.text가 dir1으로 복사된다
```

#### mv

```bash
# move
mv file.text dir2/       # file.text를 dir2로 이동
```

cp, mv 모두 폴더(경로)가 아니라 새로운 파일로 복사 ・ 이동할 수 있다
`cp` or `mv` 원하는-파일 대상-파일(또는 경로)

#### rm

```bash
# remove
rm 파일명             # 해당 파일 삭제

rm -r 디렉토리명       # 해당 폴더 삭제
```

#### grep

```bash
# Global Regular Expression Print
grep "keyword" *.txt         # keyword가 포함된 모든(*) txt파일
                             # 검색어 다음에 file.text 라면 file.text안에서 검색어를 찾음
grep -n "word" file.text     # file.text 파일에서 word가 몇번째 줄에 있는지 확인
grep -ni "word" *.txt        # 대 ・ 소문자 상관없이 찾기  (i = insenstive)
grep -nir "word" .           # 현재 경로와 그 하위에 있는 모든 서브폴더에 한해서 word를 검색한다 (r = recursive) | 보통 프로젝트 최상위 경로에서 사용한다
```

## Work with environment variables

```bash
env                      # 설정된 환경변수를 보여줘
export MY_DIR="dir1"     # 값이 dir1이고 변수명이 MY_DIR인 환경변수를 설정함
unset MY_DIR             # MY_DIR라는 환경변수를 제거함

cd $MY_DIR               # 환경변수를 사용할 땐 앞에 '$'를 붙여준다  (명령어: dir1 파일로 들어가기)
```

## Bonus

vi , vim : 터미널에서 이용되는 텍스트 에디터

```bash
vim file.txt      # file.txt 라는 파일을 만들고 vim editor 모드로 들어감

i          # 수정  ( insert )
           # 수정을 다하고 insert 모드에서 나가려면 ⎋(esc)버튼을 누른 뒤,
:wq        # 저장하고 닫기
:q         # 그냥 닫기 (수정사항 반영되지 않음)
           # w: write changes (수정한 거 저장) | q: quit (중지)
:q!        # 강제종료
```
