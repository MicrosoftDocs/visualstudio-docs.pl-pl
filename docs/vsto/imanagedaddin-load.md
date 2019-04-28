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
ms.openlocfilehash: 87fb34e90d36383f49b6369fb1dea4b9854c7300
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956734"
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
- [IManagedAddin, interfejs](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
