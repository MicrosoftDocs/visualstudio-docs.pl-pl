---
title: IWefDebuggingSupport, interfejs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a71adf5371275fbbdc19cdf09be96ef900ec073d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583766"
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport, interfejs
  Implementowany przez środowisko debugowania, takich jak Visual Studio, aby ułatwić debugowanie aplikacji dla pakietu Office. Aplikacji pakietu Office, takich jak Word lub Excel, uzyskuje dostęp do tego interfejsu z programu Visual Studio, a następnie wywołuje metody interfejsu w niektórych punktach podczas sesji debugowania.

## <a name="syntax"></a>Składnia

```csharp
[
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),
    oleautomation
]
interface IWefDebuggingSupport : IUnknown
{
    HRESULT SetWefProcessId(
        [in] DWORD dwProcessId);
    HRESULT GetAutoInsertExtensions(
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);
}
```

## <a name="methods"></a>Metody
 Poniższa tabela zawiera listę metod, które definiuje IWefDebuggingSupport, interfejs.

|Nazwa|Opis|
|----------|-----------------|
|[GetAutoInsertExtensions, metoda](../vsto/getautoinsertextensions-method.md)|Pobiera informacje o aplikacjach pakietu Office, które mają być wstawiane automatycznie podczas debugowania.|
|[SetWefProcessId, metoda](../vsto/setwefprocessid-method.md)|Zawiera identyfikator procesu, który uruchomi zawartości w ramach rozszerzenia sieci Web (WEF).|
