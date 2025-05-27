![image](https://github.com/user-attachments/assets/c65e8ac3-3035-4d9f-b7ee-41ba54029078)

## 📮 주요 링크
### 0️⃣ S3 버킷 웹사이트 엔드포인트
http://one-dawn.s3-website.ap-northeast-2.amazonaws.com

### 1️⃣ CloudFrount 배포 도메인 이름
https://d29ntnwkklcrxz.cloudfront.net

## 📌 주요 개념
### 0️⃣ GitHub Actions과 CI/CD 도구
빌드, 테스트, 배포 등의 각종 파이프라인을 실행할 수 있는 도구
`commit`, `push`, `merge` 등에 의해서 특정 브랜치에 코드가 변경된 경우 정해둔 파이프라인을 대신 수행해주고 결과물을 알려주는 역할을 한다.

현재 프로젝트에서 사용하는 예시로는 `Next.js`를 빌드하고 `S3`에 업로드하고 `CloudFront`의 캐시를 초기화하는 과정을 수행합니다.

### 1️⃣ S3와 스토리지
`S3`는 `Simple Storage Service`의 약자로, 간단한 스토리지 서비스를 제공하는 서비스
파일을 업로드하고 그 파일에 대한 접근 권한을 설정할 수 있는 서비스입니다.

현재 프로젝트에서는 `Next.js`에서 빌드된 결과물을 저장해두고 정적으로 배포하는 용도로 사용하고 있습니다.

### 2️⃣ CloudFront와 CDN
`CloudFront`는 `Content Delivery Network`의 약자로, 콘텐츠를 전 세계 여러 곳에 분산하여 제공하는 서비스
매 요청마다 원본을 가져오면 비효율적일 경우가 높기때문에 사용자와 물리적으로 가까운 곳에 캐시를 두고 요청을 처리합니다.

### 3️⃣ 캐시 무효화(Cache Invalidation)
정적인 파일이 수정되었을경우 캐시 무효화를 해주지 않으면 과거 데이터를 계속 바라보게 됩니다.
( `Next.js`의 `ISR`을 사용할때 `revalidate`를 사용하지 않으면 `DB`가 업데이트되더라도 화면이 바뀌지 않는 것처럼 ... )

### 4️⃣ Repository secret과 환경변수
`GitHub`에서 제공하는 기능으로, 비밀 정보를 저장하고 관리할 수 있는 기능
( 참고로 `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`는 `IAM`을 통해 최소한의 권한을 가진 유저의 키를 사용하고 있습니다. )

1. `AWS_ACCESS_KEY_ID`: `AWS` 접근 키
2. `AWS_REGION`: `AWS` 리전
3. `AWS_SECRET_ACCESS_KEY`: `AWS` 비밀 접근 키
4. `CLOUDFRONT_DISTRIBUTION_ID`: `CloudFront` 배포 `ID`
5. `S3_BUCKET_NAME`: `S3` 버킷 이름

## 📊 S3와 CDN 성능 비교
![image](https://github.com/user-attachments/assets/0e837a46-e66e-4676-924b-280f275c8740)