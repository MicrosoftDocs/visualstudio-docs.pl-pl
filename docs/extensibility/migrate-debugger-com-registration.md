---
title: Migrowanie 64-bitowego debugera — Rejestracja klasy COM | Microsoft Docs
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jillfra
ms.workload:
- greggm
ms.openlocfilehash: 74fbb959f8272be001aad8a576724d5eb1ad6157
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62433698"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrowanie 64-bitowego debugera — Rejestracja klasy COM

W przypadku rozszerzeń debugera, które rejestrują klasy COM w HKEY_CLASSES_ROOT przy użyciu Regasm, regsvr32 lub bezpośrednio zapisu w rejestrze i ładowane do *msvsmon.exe* (Zdalny debuger), można teraz zapewnić tę rejestrację msvsmon bez konieczności zapisywania w HKEY_CLASSES_ROOT. Ma to wpływ na starsze oceny wyrażeń debugera platformy .NET lub aparaty debugowania, które są skonfigurowane do ładowania w procesie *msvsmon.exe* .

## <a name="msvsmon-comclass-def"></a>msvsmon-COMClass-def

Aby użyć tej techniki, należy dodać * *.msvsmon-comclass-def.js* do pliku obok msvsmon (INSTALLDIR:* \Common7\IDE\Remote Debugger\x64 *).

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
