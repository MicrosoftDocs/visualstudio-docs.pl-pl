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
ms.openlocfilehash: 91c834e61452667a0af236eddb65355f23234715
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990540"
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
