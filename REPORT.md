# EduOM Report

Name: 고희주

Student id: 20170252

# Problem Analysis

강의시간에 배운 개념을 적용한다. 
page내에 slot, data, page header가 존재하고 이를 활용하여 object를 page에 저장한다.


# Design For Problem Solving

구현할 함수는 6개이다.

EduOM_CompactPage는 디스크 조각 모으기와 유사하다. external fragmentation을 방지한다.

EduOM_CreateObject는 오브젝트를 페이지에 넣는다. 필요한 용량에 따라 구별하여 오브젝트를 넣는다.

EduOM_DestroyObject 오브젝트를 삭제한다. 

EduOM_NextObject 다음 오브젝트를 찾는다.

EduOM_PrevObject 전 오브젝트를 찾는다. 

EduOM_ReadObject 오브젝트의 데이터를 읽어들인다.
## High Level

EduOM_CompactPage slotno는 compact후 가장 마지막에 넣는다. 나머지는 데이터를 카피하여 조각모으기를 한다.

EduOM_CreateObject는 nearobj와 같은 페이지에 저장하는 것을 우선으로 한다. 만약 nearobj가 없다면 다른 페이지를 찾는다.
페이지에 저장공간이 충분히 없다면 새 페이지를 할당한다.

EduOM_DestroyObject 오브젝트를 삭제하고 헤더 정보를 업데이트한다. 삭제 후 페이지에 아무것도 없다면 페이지를 삭제한다. 

EduOM_NextObject curoid가 null이라면 파일의 첫 오브젝트를 반환 아니라면 해당 id를 갖는 오브젝트를 찾고 다음 오브젝트 아이디를 반환한다.

EduOM_PrevObject EduOM_NextObject의 역순으로 작동하는 함수를 구현한다.

EduOM_ReadObject length만큼 해당 오브젝의 데이터를 읽어들인다. 만약 REMAINDER라면 모두 읽어들인다.

## Low Level

[Edu_OM_CompactPage](../Edu_OM_CompactPage.c)
[Edu_OM_CreateObject](../Edu_OM_CreateObject.c)
[Edu_OM_DestroyObject](../Edu_OM_DestroyObject.c)
[Edu_OM_NextObject](../Edu_OM_NextObject.c)
[Edu_OM_PrevObject](../Edu_OM_PrevObject.c)
[Edu_OM_ReadObject](../Edu_OM_ReadObject.c)

# Mapping Between Implementation And the Design

메뉴얼과 카이스트에서 제공하는 QNA를 참조하여 순서대로 구현하면 된다. 카이스트 QNA에는 해당 함수 구현의 예제가 포함돼 있다.