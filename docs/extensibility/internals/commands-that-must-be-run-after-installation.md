---
title: Polecenia, które muszą zostać uruchomione po instalacji | Microsoft Docs
description: Informacje o poleceniach, które muszą być uruchamiane w ramach instalacji rozszerzenia wdrożonego za pomocą pliku msi w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64eda9c95b9c469d8defc8ab0318031e9e43172a
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305042"
---
# <a name="commands-that-must-be-run-after-installation"></a>Polecenia, które muszą zostać uruchomione po instalacji
W przypadku wdrożenia rozszerzenia za pomocą pliku *MSI* należy uruchomić program **devenv/setup** w ramach instalacji, aby można było odnaleźć rozszerzenia w programie Visual Studio.

> [!NOTE]
> Informacje przedstawione w tym temacie mają zastosowanie do znajdowania *devenv.exe* w programie Visual Studio 2008 i jego wcześniejszych wersjach. Aby uzyskać informacje na temat odnajdywania *devenv.exe* z nowszymi wersjami programu Visual Studio, zobacz [wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Znajdź devenv.exe
 *devenv.exe* poszczególnych wersji można zlokalizować z wartości rejestru, które są [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zapisywane przez instalatorów, przy użyciu tabeli RegLocator i tabel AppSearch do przechowywania wartości rejestru jako właściwości. Aby uzyskać więcej informacji, zobacz [wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator wierszy tabeli do lokalizowania devenv.exe z różnych wersji programu Visual Studio

|Podpis|Główny|Klucz|Nazwa|Typ|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>AppSearch wiersze tabeli dla odpowiednich wierszy tabeli RegLocator

|Właściwość|Podpis|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Na przykład Instalator programu Visual Studio zapisuje wartość rejestru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** jako *C:\VS2008\Common7\IDE\devenv.exe*, pełną ścieżkę do pliku wykonywalnego, który musi zostać uruchomiony przez Instalatora.

> [!NOTE]
> Ponieważ kolumna typu tabeli RegLocator ma wartość 2, nie trzeba określać informacji o dodatkowych wersjach w tabeli sygnatur.

## <a name="run-devenvexe"></a>Uruchom devenv.exe
 Po uruchomieniu akcji standardowej AppSearch w instalatorze Każda właściwość w tabeli AppSearch ma wartość wskazującą plik *devenv.exe* odpowiedniej wersji programu Visual Studio. Jeśli którekolwiek z określonych wartości rejestru nie są obecne — ponieważ ta wersja programu Visual Studio nie jest zainstalowana — określona właściwość jest ustawiona na wartość null.

 Instalator Windows obsługuje uruchamianie pliku wykonywalnego, do którego wskazuje właściwość, za pomocą typu akcji niestandardowej 50. Akcja niestandardowa powinna obejmować opcje wykonywania skryptu `msidbCustomActionTypeInScript` (1024) i `msidbCustomActionTypeCommit` (512), aby upewnić się, że pakietu VSPackage został pomyślnie zainstalowany przed integracją z usługą [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Aby uzyskać więcej informacji, [Zobacz](/windows/desktop/msi/customaction-table) [Opcje wykonywania skryptu w skryptach i akcjach niestandardowych](/windows/desktop/msi/custom-action-in-script-execution-options).

 Akcje niestandardowe typu 50 określają Właściwość zawierającą plik wykonywalny jako wartość kolumny źródłowej i argumentów wiersza polecenia w kolumnie Target.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Wiersz tabeli w ramach programu w celu uruchomienia devenv.exe

|Akcja|Typ|Element źródłowy|Cel|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|

 Akcje niestandardowe muszą zostać utworzone w tabeli InstallExecuteSequence w celu zaplanowania ich wykonywania podczas instalacji. Użyj odpowiedniej właściwości w każdym wierszu kolumny Condition, aby zapobiec uruchamianiu akcji niestandardowej, jeśli ta wersja programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie jest zainstalowana w systemie.

> [!NOTE]
> Właściwości wartości null są oceniane do, `False` gdy są używane w warunkach.

 Wartość kolumny sekwencji dla każdej akcji niestandardowej zależy od innych wartości sekwencji w pakiecie Instalator Windows. Wartości sekwencji powinny być takie, aby *devenv.exe* akcje niestandardowe działały jak najbliżej bezpośrednio przed akcją standardu funkcję InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Tabela InstallExecuteSequence do zaplanowania niestandardowych akcji devenv.exe

|Akcja|Warunek|Sequence|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Zobacz też
- [Zainstaluj pakietów VSPackage z Instalator Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
