---
title: IManagedAddin::Load
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 267e2ec1b2ec2dbb5b72a100185ce6b68d455c39
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865893"
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Wywołuje się, gdy jest ładowany zarządzanych dodatku narzędzi VSTO.  
  
## <a name="syntax"></a>Składnia  
  
```csharp
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*bstrManifestURL*|Pełna ścieżka manifestu dodatku narzędzi VSTO.|  
|*pdispApplication*|Wskaźnik do interfejsu IDispatch, który reprezentuje aplikacji hosta, która jest ładowana dodatku narzędzi VSTO.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT, która wskazuje, czy metoda została ukończona pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Manifestu to plik (zazwyczaj plik XML), który zawiera informacje, które są używane do ładowania dodatku narzędzi VSTO. Na przykład manifestu, można określić lokalizację zestawu dodatków narzędzi VSTO dla programów i klasa punktu wejścia do utworzenia wystąpienia, gdy jest ładowany dodatku narzędzi VSTO.  
  
 *BstrManifestURL* parametru zawiera wartość `Manifest` wpis w **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<nazwy aplikacji >_ \Addins\\_\<identyfikator dodatku >_**  klucza rejestru dla dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [imanagedaddin — interfejs](../vsto/imanagedaddin-interface.md).  
  
 Implementowanie [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) metodę, aby wykonywać zadania takie jak Konfigurowanie zasad aplikacji domen i zabezpieczeń dla dodatku narzędzi VSTO dla programów, który jest ładowany.  
  
## <a name="see-also"></a>Zobacz także  
 [Imanagedaddin — interfejs](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
