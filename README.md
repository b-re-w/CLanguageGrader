# C Auto Grader
<pre>
 .c auto grader/tester for CNU 컴퓨터프로그래밍3
</pre>


## 프로그램 설명
- 2024-1 인공지능학과 컴퓨터프로그래밍3 수업에서 사용하기 위한 C 과제 채점기입니다.
- 빌드하기 위해서 Windows와 MSVC++ 빌드 도구, MinGW64가 필요합니다. (Visual Studio와 CLion을 설치하면 자동으로 함께 설치됩니다.)
- Windows 종속적인 터미널 커멘드를 사용했기 때문에 macOS에서 사용이 불가능합니다.
- 컴퓨터가 x-windows-949 인코딩을 사용하는 상황을 전제로 제작되었으므로, 컴퓨터가 UTF-8을 사용한다면 글자가 깨져서 나올 수 있기 때문에, 호스트 컴퓨터에서 재 빌드가 필요하며 소스&리소스 파일을 전부 UTF-8로 변환해야 합니다.

## 디렉토리 구조 설명
- ANSWER : 채점기가 사용할 테스트 케이스 정답 보관 폴더 (소스파일은 ANSWER 폴더 바로 아래에, 각 문제별 입력과 출력은 문제 이름 폴더 하위에)
- HOMEWORK : 학생들이 제출한 과제 소스코드 저장용 폴더 (하위 폴더 형태는 학번_이름 이어야 함)
- RESULT_GRADE : 채점기가 학생들의 과제에 대한 테스트를 진행하는 폴더 (최종 결과는 SCORE_OUT.html에 저장됨)
- Grader.exe : 빌드된 채점기 파일
- ICON32512_1.ico : 프로그램 아이콘 파일
- path.config : 채점기가 사용하는 MSVC와 GCC, CLANG 경로를 표기하는 설정 파일 (사용자 환경에 맞게 꼭 수정하셔야 합니다.)
- result_template.html : 채점기가 생성하는 최종 결과 파일의 템플릿

## ANSWER 폴더 설명
<pre>
과제명이 315라 할 때, 내부 폴더 구조는 아래와 같다
- 3151/
-   0.stdin
-   0.stdout
-   1.stdin
-   1.stdout
-   ...
- 3152/
- 3153/
- ...
- 3151.c
- 3152.c
- 3153.c
- ...
- compiler.setting (과제 정답 코드 채점에 사용되는 컴파일러 세팅 파일; gcc 사용시에는 필요 없음)

즉, 과제명+과제번호 형태로 폴더를 만들어 각 테스트 케이스별 stdin과 stdout을 저장하고
만일 정답 코드가 있다면 .c 파일 형태로 ANSWER 폴더에 바로 넣어주면 되는 것이다.
</pre>
#### 과제 채점용 테스트 케이스 등록 방법
- 프로그램을 켠 후 실행 모드는 과제 채점모드나 학생 확인 모드 중 어느 것을 고르더라도 상관없이 넘어간 후
- 검증식 입력 방식 선택에서 새 검증식 입력을 선택한다.
- 기존 테스트 식을 지우는 것에 동의하냐는 질문에 y를 두번 눌러 넘긴다.
##### 방법 1 - 직접 stdin과 stdout을 입력
[방법 1 영상](https://b-re-w.github.io/CLanguageGrader/etc/register_answer_1.html)
- 정답 소스 파일이 있다면 ANSWER 폴더 안에 넣어주세요 분기에서 그냥 무시하고 엔터를 누른다.
- 과제 날짜를 입력하고, 과제 개수를 입력하면 1번부터 테스트 케이스의 개수를 지정할 수 있다.
- 개수를 지정하면, 메모장이 뜨는데 그곳에 테스트 케이스의 input값을 입력하고 저장한 뒤 메모장을 끈다. (그냥 끄면 저장 안되니까 꼭 저장해야 함)
- 그럼 다시 output을 지정할 수 있는 메모장 화면이 뜨는데 이 역시 input과 동일하게 작업한다.
- 모든 과제의 모든 테스트 케이스에 대해 지정한다.
##### 방법 2 - stdin은 직접 입력하고 stdout은 소스 파일을 통해 자동 생성
[방법 2 영상](https://b-re-w.github.io/CLanguageGrader/etc/register_answer_2.html)
- 정답 소스 파일이 있다면 ANSWER 폴더 안에 넣어주세요 분기에서 잠시 멈춘 후
- 정답 소스 파일을 파일명 형식에 맞게 수정하여 ANSWER 폴더 안에 넣는다.
- 다시 프로그램으로 돌아와 엔터를 누르면 자동으로 컴파일이 진행된다.
- 과제 날짜를 입력하고, 과제 개수를 입력하면 1번부터 테스트 케이스의 개수를 지정할 수 있다.
- 개수를 지정하면, 메모장이 뜨는데 그곳에 테스트 케이스의 input값을 입력하고 저장한 뒤 메모장을 끈다. (그냥 끄면 저장 안되니까 꼭 저장해야 함)
- 그럼 자동으로 output 값을 생성해준다.
- 모든 과제의 모든 테스트 케이스에 대해 지정한다.


## HOMEWORK 폴더 설명
- HOMEWORK 하위에 각 학생들의 과제를 학번_이름 형태로 저장해둬야 합니다.
- .c 파일은 학번_이름 폴더 바로 하위에 있어야 하고, 내부에 폴더가 하나 더 있으면 인식하지 못합니다.
<pre> 폴더 구조 예시
- 202102596_김현동/
-   3151.c
-   3152.c
-   3153.c
-   3154.c
-   ...
-   compiler.setting (과제 정답 코드 채점에 사용되는 컴파일러 세팅 파일; gcc 사용시에는 필요 없음)
- 202102597_신수현/
- 202102598_전수진/
- 202102599_홍길동/
- ...
</pre>
#### 타겟 컴파일러 세팅 방법
- 사용할 수 있는 컴파일러 : GCC(기본), MSVC++, Clang
- CMAKE 빌드는 아직 지원되지 않습니다.
- 과제 파일을 압축해서 낼 때 compiler.config 파일을 포함해서 내면 컴파일러를 선택할 수 있습니다.
- compiler.config 파일이 없으면 기본 컴파일러인 GCC로 컴파일을 진행합니다.
- compiler.config 내부 (컴파일러에 맞게 입력):
<pre>
compiler = gcc
</pre>
<pre>
compiler = msvc
</pre>
<pre>
compiler = clang
</pre>


## RESULT_GRADE 폴더 설명
- 채점기를 돌리고 나면 각 학번_이름 폴더 하위에 과제, 테스트 케이스별 stdout이 저장되어 있게 됩니다.
- SCORE_OUT.html 파일을 열면 채점 결과를 정리해서 볼 수 있습니다.


## 전체 사용법
1. 최신 [release](https://github.com/b-re-w/CLanguageGrader/releases) 배포 파일을 다운받아 압축을 해제한다.
2. 학생들이 제출한 과제들을 전부 HOMEWORK 폴더 하위에 압축 해제한다. 이때, 하위 폴더의 구조는 학번_이름 형태여야 하며, 학번_이름 폴더 안에 .c코드가 바로 들어있어야 한다.
3. Grader.exe를 실행한다.
4. 실행 모드를 전체 [자동 배치모드](https://b-re-w.github.io/CLanguageGrader/etc/batch_mode.html) (교수님 채점 모드)로 사용할 것인지 아니면 [일반 모드](https://b-re-w.github.io/CLanguageGrader/etc/normal_mode.html) (학생 확인 모드)로 사용할 것인지 지정한다.
5. 새 테스트 케이스를 입력할 것인지 기존 케이스를 사용할 것인지 선택한다.
6. 프로그램이 HOMEWORK의 하위 디렉토리를 검색하여 *.cpp가 있을 경우 *.c로 모두 변경해준다.
7. 개별 학생 과제에 대해 컴파일이 자동으로 진행된다.
8. 컴파일 후 테스트 케이스 정답 stdin을 리다이렉션해 컴파일된 과제에 대입하고 결과 값을 저장한다. 결과 값은 RESULT 폴더에서 열람할 수 있다.
9. 결과 값들과 테스트 케이스 정답 stdout을 좌우공백/개행 을 무시하고 한줄 씩 비교한다.
10. 작업이 완료되면 프로그램이 종료되고 RESULT_GRADE 폴더 내부의 과제 채점 점수표 SCORE_OUT.html 파일이 브라우저에서 열린다.


## 채점 결과표 예시
[예시 채점 결과표](https://b-re-w.github.io/CLanguageGrader/src/Grader/Grader/RESULT_GRADE/SCORE_OUT.html)
