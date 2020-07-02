---
title: IManagedAddin::Load
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1307d720e005855770ee68659374dbbfae247d65
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541040"
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Wywoływana, gdy zostanie załadowany zarządzany dodatek narzędzi VSTO.

## <a name="syntax"></a>Składnia

```csharp
HRESULT Load([in] BSTR bstrManifestURL,
             [in] IDispatch *pdispApplication);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*bstrManifestURL*|Pełna ścieżka manifestu dla dodatku VSTO.|
|*pdispApplication*|Wskaźnik do elementu IDispatch, który reprezentuje aplikację hosta, która ładuje dodatek narzędzi VSTO.|

## <a name="return-value"></a>Wartość zwracana
 Wartość HRESULT wskazująca, czy metoda została ukończona pomyślnie.

## <a name="remarks"></a>Uwagi
 Manifest to plik (zazwyczaj plik XML), który zawiera informacje, które są używane do załadowania dodatku VSTO. Na przykład manifest może określać lokalizację zestawu dodatku VSTO oraz klasę punktu wejścia do wystąpienia podczas ładowania dodatku VSTO.

 Parametr *bstrManifestURL* zawiera wartość `Manifest` wpisu w kluczu rejestru **HKEY_CURRENT_USER \software\microsoft\office \\ _\<application name>_ \\ _\<add-in ID>_ \Addins** dla dodatku VSTO. Aby uzyskać więcej informacji, zobacz [IManagedAddin — Interface](../vsto/imanagedaddin-interface.md).

 Zaimplementuj metodę [IManagedAddin —:: Load](../vsto/imanagedaddin-load.md) , aby wykonać zadania, takie jak konfigurowanie domeny aplikacji i zasad zabezpieczeń dla załadowanego dodatku VSTO.

## <a name="see-also"></a>Zobacz także
- [IManagedAddin — Interfejs](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
