---
title: Polecenia uruchamiane po zakończeniu instalacji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d336e4a65178ff09f5db01dffeb5bedd3b5b946e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56631396"
---
# <a name="commands-that-must-be-run-after-installation"></a>Polecenia uruchamiane po zakończeniu instalacji
W przypadku wdrożenia rozszerzenia w ramach *.msi* pliku, należy uruchomić **devenv/Setup** jako część instalacji w kolejności dla programu Visual Studio odnaleźć rozszerzeń.

> [!NOTE]
>  Informacje przedstawione w tym temacie mają zastosowanie do wyszukiwania *devenv.exe* za pomocą programu Visual Studio 2008 i starszych wersji. Aby uzyskać informacje na temat odnajdywania *devenv.exe* przy użyciu nowszej wersji programu Visual Studio, zobacz [wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Znajdź devenv.exe
 Możesz znaleźć, każda wersja *devenv.exe* z rejestru wartości [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zapisu pliki instalacyjne, za pomocą tabeli RegLocator i AppSearch powoduje niepoprawne obcięcie tabel do przechowywania wartości rejestru jako właściwości. Aby uzyskać więcej informacji, zobacz [wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator wiersze tabeli, aby zlokalizować devenv.exe z różnych wersji programu Visual Studio

|Podpis|Główny|Key|Nazwa|Typ|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>AppSearch powoduje niepoprawne obcięcie wiersze tabeli, aby uzyskać odpowiednie wiersze tabeli RegLocator

|Właściwość|Podpis|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Na przykład, Instalator programu Visual Studio zapisuje wartość rejestru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** jako *C:\VS2008\Common7\IDE\devenv.exe*, pełną ścieżkę do pliku wykonywalnego, należy uruchomić Instalatora.

> [!NOTE]
> Ponieważ tabela RegLocator typ kolumny jest równa 2, nie jest konieczne Określ dodatkowe informacje o wersji w tabeli podpisu.

## <a name="run-devenvexe"></a>Uruchom devenv.exe
 Po zakończeniu AppSearch uruchamia akcję standardowego w Instalatorze, każdej właściwości w tabeli AppSearch powoduje niepoprawne obcięcie ma wartość wskazuje *devenv.exe* pliku odpowiednią wersję programu Visual Studio. Jeśli dowolna z wartości określonego rejestru nie są obecne — ponieważ nie zainstalowano tej wersji programu Visual Studio — określona właściwość jest ustawiona na wartość null.

 Instalator Windows obsługuje uruchamianie pliku wykonywalnego, na który wskazuje właściwość za pomocą akcji niestandardowej wpisz 50. Akcja niestandardowa powinna zawierać opcje wykonywania w skrypcie, `msidbCustomActionTypeInScript` (1024) i `msidbCustomActionTypeCommit` (512), aby upewnić się, że pakietu VSPackage został pomyślnie zainstalowany przed integrując je do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji, zobacz [Akcja niestandardowa tabela](https://docs.microsoft.com/windows/desktop/msi/customaction-table) i [opcje wykonywania w skrypcie Akcja niestandardowa](https://docs.microsoft.com/windows/desktop/msi/custom-action-in-script-execution-options).

 Niestandardowe akcje typu 50 Określ właściwości zawierające plik wykonywalny jako wartość kolumny źródłowej i argumenty wiersza polecenia, w kolumnie docelowej.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Akcja niestandardowa wiersze tabeli, aby uruchomić devenv.exe

|Akcja|Typ|Źródło|Cel|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|

 Akcje niestandardowe musi zostać utworzona do tabeli InstallExecuteSequence, aby zaplanować ich wykonanie w trakcie instalacji. Zapobiegaj akcji niestandardowej z są uruchamiane, czy za pomocą odpowiednich właściwości w każdym wierszu w kolumnie warunek wersję [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie jest zainstalowany w systemie.

> [!NOTE]
>  Właściwości zwracające wartość null, być `False` przypadku użycia w warunkach.

 Wartość kolumny sekwencji dla każdej akcji niestandardowej jest zależny od innych wartości sekwencji do pakietu Instalatora Windows. Sekwencja wartości powinny być tak, aby *devenv.exe* akcje niestandardowe, Uruchom jako najbliżej bezpośrednio przed działań standardowych InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>InstallExecuteSequence tabeli, aby zaplanować akcje niestandardowe devenv.exe

|Akcja|Warunek|Sekwencja|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Zobacz także
- [Instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)