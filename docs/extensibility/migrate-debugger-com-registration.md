---
title: Migrowanie rejestracji klasy 64-bitowych debugera COM | Dokumentacja firmy Microsoft
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jillfra
ms.workload:
- greggm
ms.openlocfilehash: 74fbb959f8272be001aad8a576724d5eb1ad6157
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712206"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrowanie 64-bitowy debuger rejestracji klasy COM

Debuger rozszerzeń, które rejestrują COM klasy w kluczu HKEY_CLASSES_ROOT za pomocą regasm, regsvr32, lub bezpośrednio zapisywania w rejestrze i ładowany do *msvsmon.exe* (zdalny debuger) jest obecnie możliwe zapewnienie to polecenie msvsmon bez konieczności pisania przekierowywanie wpisów z HKEY_CLASSES_ROOT rejestracji. Ma to wpływ na starsze ewaluatory wyrażeń debugera platformy .NET lub aparaty debugowania, które są skonfigurowane do załadowania w *msvsmon.exe* procesu.

## <a name="msvsmon-comclass-def"></a>msvsmon-comclass-def

Aby użyć tej metody, należy dodać  **.msvsmon-comclass-def.json* pliku obok polecenia msvsmon (InstallDir:* \Common7\IDE\Remote Debugger\x64*).

Poniżej przedstawiono przykładowy plik polecenia msvsmon-comclass-def, który rejestruje, jeśli jest on zarządzany i jedną klasę native:

FileName: *MyCompany.MyExample.msvsmon-comclass-def.json*

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
