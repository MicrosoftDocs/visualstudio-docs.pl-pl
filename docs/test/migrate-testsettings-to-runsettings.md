---
title: Migrowanie testsettings do runsettings
description: Dowiedz się, jak migrować testsettings do runsettings
ms.custom: SEO-VS-2020
ms.date: 03/18/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab1cfe921777fa75d4f69251668934e8d78d9bec
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2021
ms.locfileid: "106087187"
---
# <a name="upgrade-from--testsettings-to-runsettings"></a>Uaktualnij z  *. testsettings* do *. runsettings*

Plik konfiguracji testu można uaktualnić z *. testsettings* do *. runsettings* przy użyciu narzędzia SettingsMigrator, które jest instalowane wraz z programem Visual Studio. W zależności od lokalizacji instalacji programu Visual Studio można znaleźć narzędzie Ustawienia Migrator w następującej ścieżce: `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Extensions\TestPlatform\SettingsMigrator.exe`

W prawidłowej lokalizacji katalogu można uruchomić narzędzie z następującym formatem:

```console
SettingsMigrator.exe <Full path to testsettings file to be migrated>
SettingsMigrator.exe <Full path to testsettings file to be migrated> <Full path to runsettings file to be created>
```

## <a name="examples"></a>Przykłady
```console
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings E:\MyTest\MyNewRunSettings.runsettings
```

Jeśli chcesz dowiedzieć się więcej na temat sposobu konwersji opcji *. testsettings* na *. runsettings* , możesz znaleźć więcej szczegółów implementacji w [repozytorium platformy testów Open Source](https://github.com/microsoft/vstest-docs/blob/master/RFCs/0023-TestSettings-Deprecation.md#migration) w serwisie GitHub.

## <a name="see-also"></a>Zobacz też

- [Skonfiguruj przebiegi testowe z `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Uaktualnianie z MSTestv1 do MSTestv2](../test/mstest-update-to-mstestv2.md)
- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)
- [Debugowanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/debug-unit-tests-with-test-explorer.md)
