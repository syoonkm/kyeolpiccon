<h1>🌸 결마루 벚꽃 사진전 온라인 투표 웹사이트</h1>

결마루 벚꽃 사진 콘테스트의 출품작을 감상하고, 학생들이 직접 투표할 수 있는 온라인 투표 웹사이트입니다. GitHub Pages를 통해 정적 호스팅되며, Firebase를 활용해 서버 없이 투표 데이터를 수집합니다.

<h2>✨ 주요 기능</h2>

<h3>맞춤형 투표 규칙 자동 적용</h3>

- 학생들이 학번(5자리)을 입력하면 자동으로 학년과 반을 유추합니다.

- 반별 사진: 총 1장 투표 가능 (단, 본인이 속한 반은 투표 불가)

- 개인별 사진: 총 3장 투표 가능 (단, 본인 사진은 투표 불가)

<h3>멀티미디어 연동 (유튜브 & 가사)</h3>

- 개인별 사진 아래에 학생이 지정한 유튜브 음악(iframe 임베드)과 노래 가사가 함께 표시됩니다.

<h3>성능 최적화 (Lazy Loading)</h3>

- 모든 사진과 유튜브 영상에 지연 로딩(loading="lazy")을 적용하여 초기 페이지 접속 속도를 크게 개선했습니다.

<h3>클라우드 데이터베이스 연동</h3>

- Firebase Firestore를 사용하여 학생들의 투표 데이터를 실시간으로 중앙 서버에 저장합니다.

- 익명 로그인(Anonymous Auth)을 사용하여 학생들의 별도 회원가입 절차를 생략했습니다.

<h2>🛠️ 기술 스택</h2>

- Frontend: HTML5, Vanilla JavaScript, Tailwind CSS (CDN)</h3>

- Icons: Lucide Icons (CDN)</h3>

- Backend / DB: Firebase (Authentication, Firestore)</h3>

- Hosting: GitHub Pages</h3>

<h2>📁 파일 구조 및 이미지 에셋 설정</h2>

```
📦 repository-name
 ┣ 📂 images/            # 출품작 사진 폴더 (반드시 이 이름이어야 함)
 ┃ ┣ 📜 1-1.jpeg
 ┃ ┣ 📜 1-2.jpeg
 ┃ ┣ 📜 2-1.png          # 확장자에 유의 (코드 내 ext 속성과 일치해야 함)
 ┃ ┣ 📜 10101.jpeg
 ┃ ┗ ...
 ┣ 📜 index.html         # 메인 웹사이트 코드
 ┗ 📜 README.md          # 현재 문서
```
- ⚠️ 중요: GitHub Pages는 파일 이름의 대소문자와 확장자를 엄격하게 구분합니다. 실제 파일이 .JPG 또는 .JPEG인지, 코드에 등록된 확장자와 완벽히 일치하는지 반드시 확인해야 합니다.

<h2>🚀 배포 및 Firebase 설정 방법</h2>

1. Firebase 콘솔에서 새 프로젝트를 생성합니다.

2. Authentication에서 익명(Anonymous) 로그인을 활성화합니다.

3. Firestore Database를 생성하고, 규칙(Rules)을 다음과 같이 설정합니다.
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /votes/{studentId} {
      allow create, update: if true; 
      allow read, delete: if false; 
    }
  }
}
```

4. 코드에 API 키 적용
- index.html 파일 내부의 firebaseConfig 객체에 본인 프로젝트의 API 키를 입력합니다.

5. GitHub Pages 배포
- 이 코드와 images 폴더를 GitHub 저장소에 푸시(Push)하고, Settings > Pages에서 배포를 활성화합니다.
