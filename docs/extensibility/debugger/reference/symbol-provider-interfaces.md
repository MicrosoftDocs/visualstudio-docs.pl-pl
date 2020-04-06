---
title: Interfejsy dostawców symboli | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7929ba36c76f0db1cabab087afe3590de509efff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715847"
---
# <a name="symbol-provider-interfaces"></a>Symbol Provider Interfaces
Poniżej przedstawiono interfejsy obsługi [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]symboli dla pliku .

## <a name="discussion"></a>Dyskusji
 Interfejsy te są używane do oceny zmiennych w stosie wywołań w trybie przerwania. Są one implementowane tylko dla dostawców symboli środowiska uruchomieniowego języka wspólnego (SP).

|Interface|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|Sp|Reprezentuje adres elementu.|
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|Sp|Reprezentuje adres elementu, zapewniając dostęp do identyfikatora procesu.|
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|Sp|Reprezentuje symbol tablicy lub typ tablicy.|
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|Sp|Reprezentuje symbol klasy lub typ klasy.|
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|Sp|Reprezentuje dostawcę symboli COM+ z metodami specyficznymi dla kodu zarządzanego.|
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|Sp|Reprezentuje dostawcę symboli COM+ z metodami specyficznymi dla kodu zarządzanego i rozszerza **IDebugComPlusSymbolProvider**.|
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|Sp|Reprezentuje symbol lub typ, który jest kontenerem dla innych symboli lub typów.|
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|Sp|Reprezentuje atrybut niestandardowy, który może być dołączony do symbolu.|
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|Sp|Reprezentuje kwerendę dla atrybutów niestandardowych w metodzie lub typie.|
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|Sp|Zapewnia dostęp do atrybutów niestandardowych na symbolu.|
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|Sp|Interfejs podstawowy dla dowolnego typu, który można określić w czasie wykonywania.|
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|Sp|Reprezentuje pole dynamiczne dla obiektu [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)|
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|Sp|Reprezentuje typ wyliczenia.|
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Sp|Rozszerza typy dostępnych pól do obsługi kodów ogólnych kodu zarządzanego.|
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|Sp|Klasa podstawowa dla wszystkich pól; reprezentuje opis symbolu lub typu.|
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|Sp|Reprezentuje definicję pola dla typu ogólnego kodu zarządzanego.|
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|Sp|Reprezentuje wystąpienie pola dla typu ogólnego kodu zarządzanego.|
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|Sp|Reprezentuje parametr dla typu ogólnego kodu zarządzanego.|
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|Sp|Reprezentuje metodę.|
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|Sp|Reprezentuje modyfikator opcjonalny debugowania.|
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|Sp|Reprezentuje wskaźnik.|
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|Sp|Reprezentuje wartość wyliczenia typu pierwotnego z interfejsu [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)|
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|Sp|Reprezentuje właściwość klasy kodu zarządzanego, które można uzyskać lub ustawić.|
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|Sp|Reprezentuje dostawcę symboli, który udostępnia symbole i typy.|
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|Sp|Reprezentuje dostawcę symboli z bezpośrednim dostępem do metadanych i interfejsów symboli podstawowych.|
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|Sp|Reprezentuje możliwość tworzenia pola, które reprezentuje typ.|
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|Sp|Rozszerza **IDebugTypeFieldBuilder,** aby móc tworzyć typy tablic.|
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|Sp|Reprezentuje kolekcję [obiektów IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)|
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|Sp|Reprezentuje kolekcję [obiektów IDebugCustomAttribute.](../../../extensibility/debugger/reference/idebugcustomattribute.md)|
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|Sp|Reprezentuje kolekcję obiektów [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)|

## <a name="see-also"></a>Zobacz też
- [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
