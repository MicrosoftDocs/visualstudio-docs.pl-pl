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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 605c1dc7a7b0d24ba082767930fd53148cccbd95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920332"
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
