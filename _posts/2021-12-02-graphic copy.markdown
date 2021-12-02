---
layout: post
title: GI
date: 2021-12-02 23:44:08 +0900
category: Graphics
---

# GI

간접조명! 실시간으로는 불가능하고 미리 라이트맵으로 연산 해놓아야 함

# 라이트맵

GI 및 그림자 등을 포함한 라이팅 정보를 미리 연산하여 텍스처로 저장하는 기능!

모델링할때 UV채널을 만들어주지 않아 라이트맵이 깨지는 경우가 있는데 이때 모델 세팅에 Generate Lightmap UVs를 체크하면 UV가 자동 생성됨

# 실시간 GI

Light 설정 중 Realtime Lighting 이 있는데 Static 오브젝트만 적용되고 성능도 매우 많이 사용함

ProjectSetting > Graphics 에 Tier별로 CPU 사용량을 조절할 수 있음.

모바일은 그냥 끄는게 낫다!

# 라이트맵의 해상도

Lightmap Resolution : 텍셀(텍스처의 픽셀) 밀도를 나타내는 수치 

> 예를 들어 5X5 유닛의 크기 평면에 Lightmap Resolution가 10이라면 50X50 이 되어 2500개의 텍셀이 필요함!

Lightmap Size : 라이트맵 텍스처의 해상도. 만약 필요한 해상도가 더 크면 여러장의 라이트맵으로 만듦

> 라이트맵을 여러장 만들면 배칭이 깨지기 때문에 주의!! 배칭은 동일한 머테리얼을 사용하는 오브젝트의 폴리곤을 합쳐 드로우콜을 처리하는것이기 때문에
여러장의 텍스쳐는 여러 머테리얼을 만들게 되어 하나의 드로우콜로 처리가 불가능해짐

그렇다고 무작정 사이즈를 키우면 대역폭 문제를 일으키기 때문에 너무 큰 사이즈의 텍스처는 지양할것!

# Directinal Mode 

라이트맵 사이즈에 영향을 줌

두가지 선택지가 있는데 Non-Direcional과 Directional 이다.

가장 큰 차이는 노멀맵의 적용 유무.

Directional은 노멀맵을 적용하고 추가 메모리가 필요하며 픽셀 쉐이더 비용이 추가적으로 소모됨

모바일에서 쓰고싶으면 충분한 성능 검증이 필요

# Mixed Lightning > Lighting Mode

### Baked Indirect

GI만 기록되고 그림자는 기록하지 않음. Direct lighting 도 리얼타임으로 들어가고 그림자 처리도 리얼타임!

### Subtractive

정통적인 라이트맵

동적 오브젝트의 그림자와 라이트맵의 그림자 색이 달라서 그림자색을 바꿀수 있도록 설정에서 정할 수 있음

저사양 모바일 디바이스에 좋음.

### Shadowmask

그림자 영역을 별도의 텍스처로 따로 저장함. Subtractive와 다르게 그림자가 자연스러움

Subtractive보다는 성능비용이 요구되지만 품질은 괜찮아보임!

ProjectSetting에 Shadowmask Mode에서 Distance Shadowmask를 사용할 수 있는데

사용하면 Static 오브젝트도 거리에 따라 쉐도우맵을 적용함! 가까운 거리는 쉐도우맵으로 실시간 원거리는 Shadowmask로 처리하여

가까운 곳만 높은 품질로 보여주는 방법! 내 캐릭터는 Static오브젝트의 그림자를 받아 어두워진다거나!