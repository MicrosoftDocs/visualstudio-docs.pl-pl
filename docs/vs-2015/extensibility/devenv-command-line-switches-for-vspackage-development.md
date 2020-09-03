---
title: Devenv przełączniki wiersza polecenia pakietu VSPackage Development | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97ce429a7140d7b95393c2dcb8b34491b3adfefa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185280"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Przełączniki wiersza polecenia Devenv dla programowania pakietu VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] umożliwia deweloperom Automatyzowanie zadań z wiersza polecenia podczas wykonywania devenv.exe, pliku, w którym jest uruchamiane zintegrowane środowisko programistyczne (IDE) programu Visual Studio.  
  
 Zadania obejmują:  
  
- Wdrażanie aplikacji w wstępnie zaprojektowanych konfiguracjach spoza środowiska IDE.  
  
- Automatyczne Kompilowanie projektów przy użyciu wstępnie ustawionych ustawień kompilacji lub konfiguracji debugowania.  
  
- Ładowanie środowiska IDE w określonych konfiguracjach, a wszystko to poza IDE. Ponadto można dostosować środowisko IDE przy uruchamianiu.  
  
## <a name="guidelines-for-switches"></a>Wskazówki dotyczące przełączników  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Dokumentacja zawiera opis przełączników wiersza polecenia devenv na poziomie użytkownika. Aby uzyskać więcej informacji, zobacz [przełączniki wiersza polecenia devenv](../ide/reference/devenv-command-line-switches.md). Devenv obsługuje również dodatkowe przełączniki wiersza polecenia, które są przydatne w przypadku projektowania, wdrażania i debugowania pakietu VSPackage.  
  
|Przełącznik wiersza polecenia|Opis|  
|--------------------------|-----------------|  
|/safemode|Uruchamia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w trybie awaryjnym, ładując tylko domyślne środowisko IDE i usługi. Przełącznik/safemode zapobiega ładowaniu wszystkich pakietów VSPackage innych firm podczas [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uruchamiania, w związku z tym zapewniając stabilne wykonanie.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów.|  
|/resetskippkgs|Czyści wszystkie pomijanie opcji ładowania, które zostały dodane przez użytkowników, którzy chcą uniknąć ładowania problematycznych pakietów VSPackage, a następnie uruchomić polecenie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Obecność tagu SkipLoading wyłącza ładowanie elementu pakietu VSPackage. Wyczyszczenie znacznika powoduje ponowne włączenie ładowania pakietu VSPackage.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów.|  
|/rootsuffix|Uruchamiany przy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] użyciu lokalizacji alternatywnej. Następujące polecenie jest uruchamiane przez skrót utworzony przez [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Instalatora:<br /><br /> devenv/RootSuffix<br /><br /> W takim przypadku EXP identyfikuje lokalizację z określonym sufiksem, na przykład 10.0 EXP zamiast 10,0. Doświadczalne wystąpienie umożliwia debugowanie pakietu VSPackage niezależnie od wystąpienia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] używanego do pisania kodu.<br /><br /> Ten przełącznik może przyjmować dowolny ciąg, który identyfikuje lokalizację utworzoną przy użyciu VSRegEx.exe. Aby uzyskać więcej informacji, zobacz [wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md).|  
|/splash|Pokazuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ekran powitalny jako zwykły, a następnie wyświetla okno komunikatu przed wyświetleniem głównego środowiska IDE. Okno komunikatu umożliwia badanie ekranu powitalnego, aby sprawdzić, czy jest wyświetlana ikona produktu pakietu VSPackage.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie przełączników wiersza polecenia](../extensibility/adding-command-line-switches.md)   
 [Przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md)
