---
title: IWefDebuggingSupport, interfejs
description: Dowiedz się, jak używać środowiska debugowania, takiego jak Visual Studio, aby ułatwić debugowanie Microsoft Office aplikacji.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9fc319429414c8976d748a30ecdd1e164ce22b63
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962265"
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport, interfejs
  Zaimplementowane przez środowisko debugowania, takie jak Visual Studio, aby ułatwić debugowanie aplikacji pakietu Office. Aplikacja pakietu Office, taka jak Word lub Excel, uzyskuje ten interfejs z programu Visual Studio, a następnie wywołuje metody interfejsu w określonych punktach podczas sesji debugowania.

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
 W poniższej tabeli wymieniono metody, które definiuje interfejs IWefDebuggingSupport.

|Nazwa|Opis|
|----------|-----------------|
|[GetAutoInsertExtensions, Metoda](../vsto/getautoinsertextensions-method.md)|Pobiera informacje o aplikacjach pakietu Office, które mają być automatycznie wstawiane podczas debugowania.|
|[SetWefProcessId, Metoda](../vsto/setwefprocessid-method.md)|Zawiera identyfikator procesu, który będzie uruchamiał zawartość WEF (Web Extensions Framework).|
