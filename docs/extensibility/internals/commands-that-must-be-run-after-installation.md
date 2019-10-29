---
title: Polecenia, które muszą zostać uruchomione po instalacji | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e85a03c71064687fdfbacf24b7aa59cd2a47f1a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982022"
---
# <a name="commands-that-must-be-run-after-installation"></a>Polecenia, które muszą zostać uruchomione po instalacji
W przypadku wdrożenia rozszerzenia za pomocą pliku *MSI* należy uruchomić program **devenv/setup** w ramach instalacji, aby można było odnaleźć rozszerzenia w programie Visual Studio.

> [!NOTE]
> Informacje przedstawione w tym temacie mają zastosowanie do znajdowania pliku *devenv. exe* z programem Visual Studio 2008 i jego wcześniejszymi wersjami. Aby uzyskać informacje na temat odnajdywania *devenv. exe* w nowszych wersjach programu Visual Studio, zobacz [wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Znajdź devenv. exe
 Można zlokalizować *devenv. exe* każdej wersji z wartości rejestru, które [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] się pisać instalators, przy użyciu tabeli RegLocator i tabel AppSearch do przechowywania wartości rejestru jako właściwości. Aby uzyskać więcej informacji, zobacz [wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator wierszy tabeli, aby zlokalizować devenv. exe z różnych wersji programu Visual Studio

|podpisane|Pierwiastek|Key|Nazwa|Typ|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>AppSearch wiersze tabeli dla odpowiednich wierszy tabeli RegLocator

|Właściwość|podpisane|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Na przykład Instalator programu Visual Studio zapisuje wartość rejestru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** jako *C:\VS2008\Common7\IDE\devenv.exe*, pełną ścieżkę do pliku wykonywalnego Instalator musi działać.

> [!NOTE]
> Ponieważ kolumna typu tabeli RegLocator ma wartość 2, nie trzeba określać informacji o dodatkowych wersjach w tabeli sygnatur.

## <a name="run-devenvexe"></a>Uruchom devenv. exe
 Po uruchomieniu akcji standardowej AppSearch w instalatorze Każda właściwość w tabeli AppSearch ma wartość wskazującą plik *devenv. exe* dla odpowiedniej wersji programu Visual Studio. Jeśli którekolwiek z określonych wartości rejestru nie są obecne — ponieważ ta wersja programu Visual Studio nie jest zainstalowana — określona właściwość jest ustawiona na wartość null.

 Instalator Windows obsługuje uruchamianie pliku wykonywalnego, do którego wskazuje właściwość, za pomocą typu akcji niestandardowej 50. Akcja niestandardowa powinna obejmować opcje wykonywania w skrypcie, `msidbCustomActionTypeInScript` (1024) i `msidbCustomActionTypeCommit` (512), aby upewnić się, że program pakietu VSPackage został pomyślnie zainstalowany przed integracją go w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji, [Zobacz](/windows/desktop/msi/customaction-table) [Opcje wykonywania skryptu w skryptach i akcjach niestandardowych](/windows/desktop/msi/custom-action-in-script-execution-options).

 Akcje niestandardowe typu 50 określają Właściwość zawierającą plik wykonywalny jako wartość kolumny źródłowej i argumentów wiersza polecenia w kolumnie Target.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Wiersz tabeli programu w celu uruchomienia devenv. exe

|Akcja|Typ|Obiekt źródłowy|Obiektów|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|

 Akcje niestandardowe muszą zostać utworzone w tabeli InstallExecuteSequence w celu zaplanowania ich wykonywania podczas instalacji. Użyj odpowiedniej właściwości w każdym wierszu kolumny Condition, aby zapobiec uruchamianiu akcji niestandardowej, jeśli ta wersja [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie jest zainstalowana w systemie.

> [!NOTE]
> Właściwości wartości null są oceniane do `False`, gdy są używane w warunkach.

 Wartość kolumny sekwencji dla każdej akcji niestandardowej zależy od innych wartości sekwencji w pakiecie Instalator Windows. Wartości sekwencji powinny być takie, aby akcje niestandardowe *devenv. exe* działały jak najbliżej od razu przed akcją standardu funkcję InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Tabela InstallExecuteSequence do zaplanowania akcji niestandardowych devenv. exe

|Akcja|Warunek|Sequence|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Zobacz także
- [Zainstaluj pakietów VSPackage z Instalator Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)