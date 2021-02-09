---
title: Migrowanie 64-bitowego debugera — Rejestracja klasy COM | Microsoft Docs
description: Dowiedz się, jak zarejestrować klasy COM w programie msvsmon for Debugger Extensions bez zapisywania do HKEY_CLASSES_ROOT.
ms.custom: SEO-VS-2020
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jmartens
ms.workload:
- greggm
ms.openlocfilehash: adc1db57de2167ff3caa0e87e1075c8ff5b462e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886720"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrowanie 64-bitowego debugera — Rejestracja klasy COM

W przypadku rozszerzeń debugera, które rejestrują klasy COM w HKEY_CLASSES_ROOT przy użyciu Regasm, regsvr32 lub bezpośrednio zapisu w rejestrze i ładowane do *msvsmon.exe* (Zdalny debuger), można teraz zapewnić tę rejestrację msvsmon bez konieczności zapisywania w HKEY_CLASSES_ROOT. Ma to wpływ na starsze oceny wyrażeń debugera platformy .NET lub aparaty debugowania, które są skonfigurowane do ładowania w procesie *msvsmon.exe* .

## <a name="msvsmon-comclass-def"></a>msvsmon-COMClass-def

Aby użyć tej techniki, należy dodać **.msvsmon-comclass-def.js* do pliku obok msvsmon (INSTALLDIR:* \Common7\IDE\Remote Debugger\x64 *).

Poniżej znajduje się przykładowy plik msvsmon-COMClass-def, który rejestruje jedną klasę zarządzaną i jedną z klas macierzystych:

Nazwa pliku: *MyCompany.MyExample.msvsmon-comclass-def.jsna*

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
