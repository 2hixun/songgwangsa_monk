# 조계산송광사사고 인물부

한국 고전 문헌 아카이브 웹사이트입니다.  
XML 원문 데이터를 불러와 Text·Element 두 화면에서 탐색할 수 있습니다.

---

## 파일 구성

| 파일 | 역할 | 수정 여부 |
|------|------|-----------|
| `index.html` | 웹사이트 전체 (디자인·기능 포함) | 수정 불필요 |
| `data.xml` | 원문 XML 데이터 | **여기만 수정** |
| `README.md` | 이 안내문 | 필요시 수정 |

---

## GitHub Pages로 배포하기

### 1단계 — GitHub 계정 만들기
- <https://github.com> 접속 → 오른쪽 위 **Sign up** 클릭  
- 이메일·비밀번호·사용자명 입력 후 가입 완료

### 2단계 — 새 저장소(repository) 만들기
1. 로그인 후 오른쪽 위 **+** 아이콘 → **New repository** 클릭  
2. **Repository name** 칸에 영문 이름 입력 (예: `songgwangsa`)  
   - 공백 없이, 영문·숫자·하이픈만 사용  
3. 공개 범위 **Public** 선택  
4. 하단 **Create repository** 클릭

### 3단계 — 파일 업로드하기
1. 생성된 저장소 페이지에서 **uploading an existing file** 링크 클릭  
2. `index.html` · `data.xml` · `README.md` 세 파일을 창에 **끌어다 놓기**  
3. 페이지 아래 **Commit changes** 클릭

### 4단계 — GitHub Pages 켜기
1. 저장소 페이지 상단 **Settings** 탭 클릭  
2. 왼쪽 메뉴에서 **Pages** 클릭  
3. **Source** 항목에서 **Deploy from a branch** 선택  
4. **Branch** 를 `main` · `/ (root)` 로 설정 → **Save** 클릭  
5. 1~2분 후 아래 주소로 접속 가능:

```
https://[내GitHub아이디].github.io/[저장소이름]/
```

---

## XML 데이터 수정하기

### 방법 A — GitHub에서 직접 편집 (가장 간단)
1. 저장소 페이지에서 `data.xml` 파일 클릭  
2. 오른쪽 위 **연필 아이콘(✏ Edit this file)** 클릭  
3. 내용 수정  
4. 페이지 아래 **Commit changes** 클릭  
5. 잠시 후(보통 1분 이내) 웹사이트에 자동 반영

### 방법 B — 로컬에서 편집 후 재업로드
1. 저장소에서 `data.xml` 파일 클릭 → **Download raw file** 로 다운로드  
2. 메모장·VS Code 등 텍스트 편집기로 수정 후 저장  
3. 저장소 페이지 → **Add file** → **Upload files**  
4. 수정한 `data.xml` 업로드 → **Commit changes**

---

## XML 구조 안내

```xml
<Book>                        <!-- 전체 문헌 -->
  <Volume id="V2">            <!-- 권(卷) -->
    <Part id="인물부">         <!-- 부(部) -->
      <Chapter id="GR">       <!-- 장(章) -->
        <Section id="GR-01">  <!-- 절(節) -->
          <Content id="GR-01-01">  <!-- 개별 항목 -->
            <Quote> ... </Quote>   <!-- 인용문 -->
            <Reference> ... </Reference>  <!-- 참고 -->
          </Content>
        </Section>
      </Chapter>
    </Part>
  </Volume>
</Book>
```

### 태그 내 엔티티 8종

| 태그 | 유형 | 주요 속성 |
|------|------|-----------|
| `<Monk>` | 승려 | `beopmyeong` `beopho` `birth` `death` |
| `<Person>` | 인물 | `ja` `ho` `birth` `death` |
| `<Temple>` | 사찰 | `hanjaname` `previousname` `region` |
| `<Place>` | 장소 | `hanjaname` `previousname` `province` |
| `<Book>` | 문헌 | `hanjaname` `type` `writer` `editer` |
| `<Work>` | 작품 | `hanjaname` `type` `writer` |
| `<Object>` | 유물 | `hanjaname` `type` |
| `<Concept>` | 개념 | `id` |

---

## 로컬 미리보기 (선택사항)

웹 브라우저에서 `index.html`을 **직접 열면** 보안 정책으로 인해  
`data.xml`을 불러올 수 없어 빈 화면이 나타납니다.

로컬에서 테스트하려면 아래 방법 중 하나를 사용하세요.

**VS Code 사용 시 (추천)**
1. VS Code에서 폴더 열기  
2. 확장(Extensions)에서 **Live Server** 설치  
3. `index.html` 우클릭 → **Open with Live Server**

**Python 사용 시**
```bash
python -m http.server 8000
# 브라우저에서 http://localhost:8000 접속
```
