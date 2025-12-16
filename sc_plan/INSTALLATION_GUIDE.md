# SuperClaude Phase Tracking - 설치 가이드

---

경로 `C:\Users\{사용자 이름}\.claude\commands\sc\`

### 📋 설치된 명령어 목록

**계획 관리:**
- `/sc:plan-load` - 계획서 파일 파싱 및 등록
- `/sc:plan-list` - 등록된 계획 목록 표시
- `/sc:plan-switch` - 활성 계획 전환

**실행 제어:**
- `/sc:plan-start` - Phase 시작 및 /sc:implement 연동
- `/sc:plan-complete` - Phase 완료 처리
- `/sc:plan-next` - 다음 작업 조회

**조회:**
- `/sc:plan-status` - 전체 진행 현황 표시
- `/sc:plan-tasks` - 특정 Phase 태스크 조회

**복구:**
- `/sc:plan-rollback` - Phase 상태 롤백
- `/sc:plan-redesign` - Phase 재설계 및 영향 분석

---

## 🚀 빠른 시작

### 1. 계획서 작성

마크다운 형식으로 계획서를 작성하세요:

```markdown
## 구현 순서

### Phase 1-1: 기반 시스템 (1~2일)
- [ ] 프로젝트 설정
- [ ] GameManager 싱글톤
- [ ] SafeAreaManager
- [ ] 기본 씬 구조

### Phase 1-2: 플레이어 시스템 (2~3일)
- [ ] Player 씬/스크립트
- [ ] 터치 입력 (드래그 이동)
- [ ] 자동 사격 시스템
```

### 2. 계획 등록

```bash
/sc:plan-load docs/Design_Phase1.md
```

### 3. 진행 현황 확인

```bash
/sc:plan-status
```

### 4. Phase 시작

```bash
/sc:plan-start Phase 1-1
```

자동으로 `/sc:implement`가 호출되어 구현을 도와줍니다!

### 5. Phase 완료

```bash
/sc:plan-complete Phase 1-1
```

---

## 📁 프로젝트 구조

Phase Tracking 사용 시 생성되는 파일:

```
your-project/
├── .superclaud/
│   └── progress.yaml          # Phase 진행 상태 (자동 생성)
├── docs/
│   └── Design_Phase1.md       # 원본 계획서 (사용자 작성)
```

**참고**: `.superclaud/progress.yaml`은 자동으로 생성되며 직접 수정하지 마세요.

---

## 🔧 Serena MCP 연동

Phase Tracking은 Serena MCP를 사용하여 세션 간 상태를 유지합니다.

**Serena MCP가 설치되어 있지 않다면:**

```bash
# Serena MCP 설치 (필요 시)
npm install -g @serena/mcp-server
```

Serena Memory에 저장되는 정보:
- `plan_meta.md` - 계획 메타정보
- `plan_progress.md` - 현재 진행 상태
- `plan_history.md` - 변경 이력

---

## 📖 상세 문서

자세한 사용법은 다음 문서를 참고하세요:

- **[PHASE_TRACKING_OVERVIEW.md](./PHASE_TRACKING_OVERVIEW.md)** - 기능 소개 및 사용 가이드
- **[PHASE_TRACKING_COMMANDS.md](./PHASE_TRACKING_COMMANDS.md)** - 명령어 레퍼런스
- **[PHASE_TRACKING_SPEC.md](./PHASE_TRACKING_SPEC.md)** - 기술 명세서

---

## ✨ 명령어 자동완성

이제 Claude Code에서 `/sc:plan-`을 입력하면 모든 Phase Tracking 명령어가 자동완성 목록에 표시됩니다!

```
/sc:plan-    ← Tab 키를 누르면
├── /sc:plan-load
├── /sc:plan-status
├── /sc:plan-start
├── /sc:plan-complete
└── ...
```

---

## 🎯 일반적인 워크플로우

```
1. 계획서 작성 (마크다운)
   ↓
2. /sc:plan-load docs/plan.md
   ↓
3. /sc:plan-status (현황 확인)
   ↓
4. /sc:plan-start Phase 1-1
   ↓ (자동으로 /sc:implement 호출)
5. 작업 수행
   ↓
6. /sc:plan-complete Phase 1-1
   ↓
7. 반복 (다음 Phase)
```

---

## 🆘 문제 해결

### 명령어가 보이지 않는 경우

Claude Code를 재시작하세요:
1. Claude Code 종료
2. 다시 실행
3. `/sc:plan-` 입력 후 Tab 키로 확인

### 계획서 파싱 실패

계획서 형식을 확인하세요:
```markdown
## 구현 순서          ← 섹션 헤더 필수

### Phase X-Y: 이름   ← Phase 형식 준수
- [ ] 태스크          ← 체크리스트 형식
```

### 상태 파일 오류

`.superclaud/progress.yaml`을 삭제하고 다시 로드:
```bash
rm .superclaud/progress.yaml
/sc:plan-load docs/plan.md
```

---

## 🎉 축하합니다!

Phase Tracking 설치가 완료되었습니다. 이제 체계적인 프로젝트 관리를 시작하세요!

**다음 단계:**
1. 프로젝트 계획서 작성
2. `/sc:plan-load` 명령으로 등록
3. `/sc:plan-status`로 현황 확인
4. 첫 Phase 시작!

---

**문의 및 피드백:**
문제가 발생하거나 개선 사항이 있다면 GitHub Issues에 보고해주세요.
