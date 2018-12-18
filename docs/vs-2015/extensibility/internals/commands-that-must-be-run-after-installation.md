---
title: Polecenia uruchamiane po zakończeniu instalacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90ce272270ffd511ee3b0efe8a711730ccdb92b5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724195"
---
# <a name="commands-that-must-be-run-after-installation"></a>Polecenia, które należy uruchomić po instalacji
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Jeśli rozszerzenie zostanie wdrożony przy użyciu pliku msi, musisz uruchomić `devenv /setup` jako część instalacji w kolejności dla programu Visual Studio odnaleźć rozszerzeń.  
  
> [!NOTE]
>  Informacje przedstawione w tym temacie dotyczą znajdowanie DevEnv za pomocą programu Visual Studio 2008 i starszych wersji. Aby uzyskać informacje o tym, jak odnaleźć DevEnv przy użyciu nowszej wersji programu Visual Studio, zobacz [wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Znajdowanie devenv.exe  
 Możesz znaleźć, każda wersja devenv.exe z rejestru wartości [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zapisu pliki instalacyjne, za pomocą tabeli RegLocator i AppSearch powoduje niepoprawne obcięcie tabeli do przechowywania wartości rejestru jako właściwości. Aby uzyskać więcej informacji, zobacz [wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator wiersze tabeli, aby zlokalizować devenv.exe z różnych wersji programu Visual Studio  
  
|Signature_|Główny|Key|Nazwa|Typ|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>AppSearch powoduje niepoprawne obcięcie wiersze tabeli, aby uzyskać odpowiednie wiersze tabeli RegLocator  
  
|Właściwość|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Na przykład, Instalator programu Visual Studio zapisuje wartość rejestru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** jako **C:\VS2008\Common7\IDE\devenv.exe**, pełną ścieżkę do pliku wykonywalnego, należy uruchomić Instalatora.  
  
 **Uwaga** , ponieważ kolumna typu RegLocator jest równa 2, nie jest konieczne określić dodatkowe informacje o wersji w tabeli podpisu.  
  
## <a name="running-devenvexe"></a>Uruchamianie devenv.exe  
 Po zakończeniu AppSearch powoduje niepoprawne obcięcie uruchomieniu standardowych działań w Instalatorze każdej właściwości w tabeli AppSearch powoduje niepoprawne obcięcie ma wartość, wskazując plik devenv.exe dla odpowiedniej wersji programu Visual Studio. Jeśli dowolna z wartości określonego rejestru nie są obecne — ponieważ nie zainstalowano tej wersji programu Visual Studio — określona właściwość jest ustawiona na wartość null.  
  
 Instalator Windows obsługuje uruchamianie pliku wykonywalnego, na który wskazuje właściwość za pomocą akcji niestandardowej wpisz 50. Akcja niestandardowa powinna zawierać opcje wykonywania w skrypcie, msidbCustomActionTypeInScript (1024) i msidbCustomActionTypeCommit (512), aby upewnić się, że pakietu VSPackage został pomyślnie zainstalowany przed integrując je do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Aby uzyskać więcej informacji zobacz tabelę Akcja niestandardowa i opcje wykonywania w skrypcie akcji niestandardowych.  
  
 Niestandardowe akcje typu 50 Określ właściwości zawierające plik wykonywalny jako wartość kolumny źródłowej i argumenty wiersza polecenia, w kolumnie docelowej.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>Akcja niestandardowa wiersze tabeli, aby uruchomić devenv.exe  
  
|Akcja|Typ|Źródło|Docelowy|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/ Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/ Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/ Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/ Setup|  
  
 Akcje niestandardowe musi zostać utworzona do tabeli InstallExecuteSequence, aby zaplanować ich wykonanie w trakcie instalacji. Zapobiegaj akcji niestandardowej z są uruchamiane, czy za pomocą odpowiednich właściwości w każdym wierszu w kolumnie warunek wersję [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nie jest zainstalowany w systemie.  
  
> [!NOTE]
>  `Null` właściwości oceny do `False` przypadku użycia w warunkach.  
  
 Wartość kolumny sekwencji dla każdej akcji niestandardowej jest zależny od innych wartości sekwencji do pakietu Instalatora Windows. Sekwencja wartości powinny być akcje niestandardowe devenv.exe, Uruchom jako najbliżej bezpośrednio przed działań standardowych InstallFinalize.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>InstallExecuteSequence tabeli, aby zaplanować akcje niestandardowe devenv.exe  
  
|Akcja|Warunek|Sekwencja|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Zobacz też  
 [Instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

