---
title: Polecenia, które muszą być uruchamiane po instalacji | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 77add5afd5d44358f0077a11bb70559a796e74c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709472"
---
# <a name="commands-that-must-be-run-after-installation"></a>Polecenia, które muszą być uruchomione po instalacji
Jeśli rozmieszczenia rozszerzenia za pośrednictwem pliku *msi,* należy uruchomić **devenv /setup** jako część instalacji, aby program Visual Studio odnajdywać rozszerzenia.

> [!NOTE]
> Informacje zawarte w tym temacie dotyczy znajdowania *programu devenv.exe* w programie Visual Studio 2008 i wcześniejszych. Aby uzyskać informacje dotyczące sposobu odnajdywanie *programu devenv.exe* w nowszych wersjach programu Visual Studio, zobacz [Wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Znajdź devenv.exe
 *Devenv.exe* każdej wersji można zlokalizować z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wartości rejestru zapisywanych przez instalatorów, używając tabeli RegLocator i AppSearch do przechowywania wartości rejestru jako właściwości. Aby uzyskać więcej informacji, zobacz [Wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator wierszy tabeli, aby zlokalizować devenv.exe z różnych wersji programu Visual Studio

|Sygnatura|Główny|Klucz|Nazwa|Typ|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|OPROGRAMOWANIE\Microsoft\VisualStudio\7.0\Setup\VS|Ścieżka środowiska|2|
|RL_DevenvExe_2003|2|OPROGRAMOWANIE\Microsoft\VisualStudio\7.1\Setup\VS|Ścieżka środowiska|2|
|RL_DevenvExe_2005|2|OPROGRAMOWANIE\Microsoft\VisualStudio\8.0\Setup\VS|Ścieżka środowiska|2|
|RL_DevenvExe_2008|2|OPROGRAMOWANIE\Microsoft\VisualStudio\9.0\Setup\VS|Ścieżka środowiska|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Wiersze tabeli AppSearch dla odpowiednich wierszy tabel reglocatora

|Właściwość|Sygnatura|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Na przykład instalator programu Visual Studio zapisuje wartość rejestru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** jako *C:\VS2008\Common7\IDE\devenv.exe*, pełną ścieżkę do pliku wykonywalnego, który instalator musi uruchomić.

> [!NOTE]
> Ponieważ kolumna Typ tabeli RegLocator ma 2, nie jest konieczne określenie dodatkowych informacji o wersji w tabeli Podpis.

## <a name="run-devenvexe"></a>Uruchom plik devenv.exe
 Po uruchomieniu akcji standardowej AppSearch w instalatorze każda właściwość w tabeli AppSearch ma wartość wskazującą plik *devenv.exe* dla odpowiedniej wersji programu Visual Studio. Jeśli którakolwiek z określonych wartości rejestru nie są obecne — ponieważ ta wersja programu Visual Studio nie jest zainstalowana — określona właściwość jest ustawiona na wartość null.

 Instalator Windows obsługuje uruchamianie pliku wykonywalnego, do którego właściwość wskazuje za pomocą niestandardowego typu akcji 50. Akcja niestandardowa powinna zawierać opcje wykonywania `msidbCustomActionTypeInScript` w skrypcie `msidbCustomActionTypeCommit` (1024) i (512), aby upewnić [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]się, że vspackage został pomyślnie zainstalowany przed łączeniem go do . Aby uzyskać więcej informacji, zobacz [Tabela CustomAction](/windows/desktop/msi/customaction-table) i [Opcje wykonywania akcji niestandardowej w skrypcie](/windows/desktop/msi/custom-action-in-script-execution-options).

 Akcje niestandardowe typu 50 określają właściwość zawierającą plik wykonywalny jako wartość argumentów kolumny Źródło i wiersza polecenia w kolumnie Cel.

### <a name="customaction-table-rows-to-run-devenvexe"></a>CustomAction wiersze tabeli do uruchomienia devenv.exe

|Akcja|Typ|Element źródłowy|Środowisko docelowe|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|

 Akcje niestandardowe muszą być autorstwa w InstallExecuteSequence tabeli zaplanować je do wykonania podczas instalacji. Użyj odpowiedniej właściwości w każdym wierszu Condition kolumny, aby zapobiec akcji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] niestandardowej jest uruchamiany, jeśli ta wersja nie jest zainstalowany w systemie.

> [!NOTE]
> Właściwości o wartości null `False` są obliczane, gdy są używane w warunkach.

 Wartość kolumny Sekwencja dla każdej akcji niestandardowej zależy od innych wartości sekwencji w pakiecie Instalatora Windows. Wartości sekwencji powinny być takie, aby akcje *niestandardowe devenv.exe* były uruchamiane jak najbliżej bezpośrednio przed akcją standardową InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>InstallExequence tabeli zaplanować devenv.exe akcji niestandardowych

|Akcja|Warunek|Sequence|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Zobacz też
- [Instalowanie pakietów VSPackages za pomocą Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
