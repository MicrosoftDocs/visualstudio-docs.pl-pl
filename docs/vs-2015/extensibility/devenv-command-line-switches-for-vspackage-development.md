---
title: Przełączniki wiersza polecenia Devenv dla programowania pakietu VSPackage | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 8a32606b97e2831c2074c1feeaa71e74c116fdc4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54791046"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Przełączniki wiersza polecenia Devenv dla programowania pakietu VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Umożliwia deweloperom Automatyzowanie zadań przy użyciu wiersza polecenia podczas wykonywania devenv.exe, plik, który uruchamia program Visual Studio zintegrowane środowisko programistyczne (IDE).  
  
 Zadania obejmują:  
  
-   Wdrażanie aplikacji w wstępnie zdefiniowanych konfiguracji z poza IDE.  
  
-   Automatyczne kompilowanie projektów za pomocą wstępnie ustawionych ustawienia kompilacji lub konfiguracji debugowania.  
  
-   Ładowanie środowiska IDE w określonej konfiguracji, wszystko poza IDE. Ponadto można dostosować środowisko IDE po uruchomieniu.  
  
## <a name="guidelines-for-switches"></a>Wytyczne dotyczące przełączników  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dokumentacji opisano przełączniki wiersza polecenia devenv na poziomie użytkownika. Aby uzyskać więcej informacji, zobacz [przełączników wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md). Devenv obsługuje również dodatkowe przełączniki wiersza polecenia, które są przydatne w przypadku pakietu VSPackage programowania, wdrażania i debugowania.  
  
|Przełącznik wiersza polecenia|Opis|  
|--------------------------|-----------------|  
|/safemode|Uruchamia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w trybie awaryjnym, ładowanie tylko domyślne środowisko IDE i usługi. Przełącznik/safemode uniemożliwia załadowanie, kiedy wszystkich innych pakietów VSPackage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozpoczyna się, co pozwala na zapewnienie stabilne wykonywania.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów.|  
|/resetskippkgs|Czyści wszystkie pominąć opcje ładowania, które zostały dodane przez użytkowników, którzy chcą uniknąć ładowanie pakietów VSPackage problematyczne, następnie rozpoczyna [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Obecność tagu SkipLoading powoduje wyłączenie ładowania pakietu VSPackage. Czyszczenie tagu włączające ładowania pakietu VSPackage.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów.|  
|/rootsuffix|Uruchamia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] za pomocą alternatywnej lokalizacji. Następujące polecenie jest uruchamiane przez skrót utworzony przez [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Instalatora:<br /><br /> Devenv /RootSuffix exp<br /><br /> W tym przypadku exp identyfikuje lokalizację przy użyciu określonego sufiksu, na przykład 10.0Exp zamiast 10.0. Wystąpienie eksperymentalne umożliwia debugowanie pakietu VSPackage niezależnie od wystąpienia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] używanym do pisania kodu.<br /><br /> Ten przełącznik może być dowolny ciąg, który identyfikuje lokalizacji, do której zostały utworzone przy użyciu VSRegEx.exe. Aby uzyskać więcej informacji, zobacz [wystąpienie doświadczalne](../extensibility/the-experimental-instance.md).|  
|/splash|Pokazuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ekran powitalny w zwykły sposób, a następnie wyświetli okno wiadomości przed wyświetleniem głównego środowiska IDE. W oknie komunikatu umożliwia badanie ekran powitalny, pod kątem ikoną produktu pakietu VSPackage, przykład.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie przełączników wiersza polecenia](../extensibility/adding-command-line-switches.md)   
 [Przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md)
