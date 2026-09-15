# 전투 이미지 제작 기록 (v20)

v19에서 0~2차 전용 무기 16종과 전투 효과 16프레임을 추가했습니다. [v19 이미지·직업 연결·제작 프롬프트](V19.md)

v22에서 직업마다 다른 캐릭터 이미지와 새 길드 내부 배경을 추가했고, v23에서 실제 아틀라스 순서와 게임 직업 매칭을 수정했습니다. v24에서는 사용하지 않는 이전 도트 이미지와 모션 시트를 배포본에서 제거했고, v25에서 구형 무기 아틀라스와 전투 투명화 버그를 정리했습니다. [v22 직업별 모션·길드 내부](V22.md) · [v23 매칭 수정](V23.md) · [v25 정리 기록](V25.md)

일반 몬스터 16종과 해안 배경도 추가했습니다. [전체 의뢰·등장 몬스터·추가 이미지 제작 기록](ENCOUNTERS.md)

내장 imagegen 도구로 제작했습니다. 게임에서 원본 PNG의 해당 칸을 읽어 표시하며, 투명도를 보존합니다. 최종 채택한 파일만 배포에 포함했습니다.

| 파일 | 구성 | 게임에서 사용 |
|---|---|---|
| [bosses-v18.png](bosses-v18.png) | 투명 5×5, 네임드 25종 | named-0~named-24 순서. 네임드 토벌에서만 사용 |
| [backgrounds-v18.png](backgrounds-v18.png) | 2×3, 배경 6종 | 숲·상단길·광산·폐허·성소·화산 |
| [combat-fx-v19.png](combat-fx-v19.png) | 투명 4×4, 효과 16프레임 | 베기·타격·마법·회복 각 4프레임 |
| [normal-monsters-v19.png](normal-monsters-v19.png) | 투명 4×4, 일반 몬스터 16종 | 일반·협동·수집 의뢰 |
| [coast-v19.png](coast-v19.png) | 해안 배경 | 보물선 잔해 탐색·해양 네임드 토벌 |
| [mercenary-jobs-v22.png](mercenary-jobs-v22.png) | 투명 6×6, 36개 캐릭터 | 직업마다 다른 무기·복장·실루엣 |
| [guild-interior-v22.png](guild-interior-v22.png) | 탑뷰 길드 내부 | 전투관전과 같은 픽셀 질감의 길드 맵 |

무기는 관전용 외형입니다. 기존 장비 능력치와 내구도, 임무 성공률 계산을 유지합니다. 관전 동작은 시간제 의뢰 진행을 보여주는 연출이며, 별도 타격 판정이나 실시간 피해 계산을 추가하지 않았습니다.

## 최종 제작 프롬프트

### 네임드 몬스터

Production game sprite atlas, transparent PNG alpha background, square 5 columns by 5 rows EXACT evenly spaced grid. Tiny full-body pixel-art monsters centered in each cell, each creature ONLY HALF of its cell size. Very wide EMPTY TRANSPARENT GUTTERS between every monster. All sprites occupy only central 50% of cells, no wings/weapons cross cells. No background drawing, no checkerboard, no text, no borders. Fantasy 32-bit pixel art facing left. Exact row-major list: row1 goblin king crown cleaver; orc warlord axe; hobgoblin general spear; minotaur shaman staff; lizard king trident. Row2 silver werewolf; blue troll shaman; purple ogre mage; cyclops chief; arachne spider queen. Row3 queen ent tree spirit; silver Bahamut dragon; five-headed Tiamat dragon; black Ancalagon dragon; green Fafnir dragon. Row4 purple Behemoth horned beast; blue Leviathan sea serpent; purple Kraken; winged scorpion-lion Manticore; goat-lion-snake Chimera. Row5 crowned skeleton Lich King; headless armored Dullahan with helmet in hand; red caped vampire lord; Beowulf greatsword warrior; red Dragon Lord golden armor. 25 full figures, exact grid, lots of transparent padding. The empty margins are essential because this sheet is automatically cropped into equal square cells.

### 배경

Use case stylized-concept. Production fantasy RPG pixel-art BACKGROUND ATLAS. One landscape image, EXACT equal 2 columns by 3 rows, SIX panels edge-to-edge, no borders no gaps no labels no text. Each panel a wide side-view battlefield, detailed scenic background but clear level empty foreground in bottom 40% for game characters to stand. No characters no monsters no weapons. Consistent polished 32-bit pixel art with crisp textured foliage stone and atmospheric light. Row1 left: ancient emerald forest clearing moss stones huge trees. Row1 right: golden trade road distant hills timber bridge, NO cart. Row2 left: luminous cyan crystal mine cave with ore veins timber beams. Row2 right: ruined stone courtyard broken columns at blue dusk. Row3 left: arcane shrine glowing violet runes blue magical pool. Row3 right: volcanic dragon arena basalt floor distant red lava mountains. Six exact equal rectangular cells suitable for automatic cropping at width/2 and height/3. 2048x1536 or same 4:3 ratio. Fill each cell fully.

### 직업별 무기

Use case stylized-concept. Production transparent PNG fantasy pixel art weapon atlas EXACT 5 columns x 4 rows, 20 equal cells. One isolated weapon centered per cell with 16 percent padding, never crossing cells. Consistent polished 32-bit pixel art, crisp silhouette, diagonal up-right, no characters, hands, labels, text, borders, shadows or backdrop. True transparent background. Row-major order: row1 silver blue dragon spear; black violet runeblade sword; golden warhammer; crimson double axe; green thorn bow. Row2 precision crossbow; turquoise wind bow; lightning longbow; crimson assassin dagger; silver crescent dagger. Row3 golden chakram; bronze coiled whip; blue crystal mage staff; multicolored elemental staff; green skull necromancer staff. Row4 purple occult grimoire; ivory healing staff; gold eye oracle scepter; broad silver gold paladin sword; flaming inquisitor mace. Exact clean five by four grid. All full objects visible. Aspect ratio 5:4.

## 검증

- 네임드 25종과 3차 직업 무기 20종의 연결 확인
- 길드 맵·관전 화면·참가자 버튼에서 용병 상세 이동 확인
- 이전 저장 데이터의 자금·시간·용병과 구직업 이름 변환 확인
- 자정을 넘는 임무와 야간 스킵, 토벌 보상·칭호·트로피 확인
- 390px 모바일 화면, 일시정지 동작, 이미지가 포함된 단일 HTML의 오프라인 실행 확인

이전 임시 도형으로 적과 배경을 그리던 관전 코드를 교체했습니다. 관전 패널이 숨겨져 있거나 표시 내용이 동일할 때 불필요하게 다시 만드는 작업을 줄였습니다. 저장 형식과 기존 게임 규칙은 유지합니다.


v26에서는 전투 화면의 무기 휘두르기 도형과 임시 대기 실루엣을 제거하고, 직업별 전투 이미지를 원본 모습 그대로 표시합니다. [v26 전투 이미지 정리](V26.md)

v27에서는 원본 전투 이미지를 유지한 채 부드러운 연속 모션을 적용했습니다. [v27 전투 모션 정리](V27.md)


v28에서는 용병 이름 중복을 자동 정리하고, 모든 시설의 최대 레벨을 길드 건물 레벨에 맞췄습니다. [v28 이름·시설 레벨 정리](V28.md)


v29에서는 직업 초상화 아틀라스 로드 완료 후 용병 목록과 상세 패널을 자동으로 다시 그려 초상화가 빠지지 않게 했습니다. [v29 용병 초상화 로딩 수정](V29.md)


v30에서는 길드 평판 단계에 따른 귀족 의뢰와 희귀 용병·상위 상점을 해금하고, 머리·몸통·손·발·장신구를 포함한 부위별 장비 슬롯과 전투력 반영을 추가했습니다. 전투 귀환 결과에는 참가자별 전투력 기여도와 성공률·보상을 기록하며, 고정파티는 이름 변경·리더 지정·전열/화력/지원/정찰 역할을 직접 배치할 수 있습니다. [v30 길드 시스템 확장](V30.md)
