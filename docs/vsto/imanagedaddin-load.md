---
title: IManagedAddin::Load
description: Wywoływana, gdy zostanie załadowany zarządzany dodatek narzędzi VSTO.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fc89ba13e9fc0f62b264cdb926e1a8392c0b41bd
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469765"
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

 Parametr *bstrManifestURL* zawiera wartość `Manifest` wpisuHKEY_CURRENT_USER\Software\Microsoft\Officew kluczu rejestru **\\ _\<application name>_ \Addins \\ _\<add-in ID>_** dla dodatku VSTO. Aby uzyskać więcej informacji, zobacz [IManagedAddin — Interface](../vsto/imanagedaddin-interface.md).

 Zaimplementuj metodę [IManagedAddin —:: Load](../vsto/imanagedaddin-load.md) , aby wykonać zadania, takie jak konfigurowanie domeny aplikacji i zasad zabezpieczeń dla załadowanego dodatku VSTO.

## <a name="see-also"></a>Zobacz też
- [IManagedAddin — Interfejs](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
