---
title: Symbol interfejsy dostawcy | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c409175fb39207bc0e83a521577ad6d641731691
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204869"
---
# <a name="symbol-provider-interfaces"></a>Symbol Provider Interfaces
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Poniżej przedstawiono interfejsy obsługi symboli dla [!INCLUDE[vsipsdk](../../../includes/vsipsdk-md.md)].  
  
## <a name="discussion"></a>Dyskusja  
 Te interfejsy są używane do oceny zmiennych w stosie wywołań w trybie break. Są one wykonywane tylko w przypadku wspólnego języka środowiska uruchomieniowego symbol dostawców (SP).  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Reprezentuje adres elementu.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Reprezentuje adres elementu, zapewniając dostęp do identyfikatora procesu.|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Reprezentuje symbol tablicy lub typu tablicowego.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Reprezentuje symbol klasy lub typu klasy.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Reprezentuje dostawcę symbol modelu COM +, za pomocą metod, które są specyficzne dla kodu zarządzanego.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Reprezentuje dostawcę symbol modelu COM +, za pomocą metod, które są specyficzne dla kodu zarządzanego i rozszerza **IDebugComPlusSymbolProvider**.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Reprezentuje symbol lub typ, który jest kontenerem dla innych symboli lub typów.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Reprezentuje atrybut niestandardowy, który można dołączyć do określonego symbolu.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Reprezentuje zapytanie, w przypadku niestandardowych atrybutów na metody lub typu.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Umożliwia dostęp do atrybutów niestandardowych, które symbol.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Podstawowy interfejs dla dowolnego typu, który można określić w czasie wykonywania.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Reprezentuje dynamiczne pole dla [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) obiektu.|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Reprezentuje typ wyliczenia.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|SP|Rozszerza typy dostępnych pól, które obsługują elementy ogólne kodu zarządzanego.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Klasa bazowa dla wszystkich pól; reprezentuje opis symbolu lub typu.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Reprezentuje definicję pola dla kodu zarządzanego typu ogólnego.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Reprezentuje wystąpienie pola dla kodu zarządzanego typu ogólnego.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Reprezentuje parametr typu ogólnego kodu zarządzanego.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Reprezentuje metodę.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Reprezentuje opcjonalny modyfikator właściwy debugowania.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Reprezentuje wskaźnik.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Reprezentuje wartość wyliczenia typu podstawowego z [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu.|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Reprezentuje właściwość klasy kodu zarządzanego, który może mieć postać get lub ustawić.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Reprezentuje dostawcę symbol, który zawiera symbole i typy.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Reprezentuje dostawcę symbol bezpośredni dostęp do metadanych i podstawowych interfejsów symboli.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Reprezentuje zdolność do tworzenia pola, które reprezentuje typ.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Rozszerza **IDebugTypeFieldBuilder** aby można było utworzyć typy tablic.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Reprezentuje kolekcję [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiektów.|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Reprezentuje kolekcję [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) obiektów.|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Reprezentuje kolekcję [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
