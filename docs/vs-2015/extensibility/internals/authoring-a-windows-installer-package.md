---
title: Tworzenie pakietu Instalatora Windows | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5743caf2d45e8a2c06e841c68da2e8a3fcb222d1
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54833860"
---
# <a name="authoring-a-windows-installer-package"></a>Tworzenie pakietu Instalatora Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Danych zależy od modelu Instalatora Windows. Zamiast pisania procedurach skryptu, aby skopiować pliki i Zapisz wpisy rejestru, na przykład, możesz tworzyć wierszy i kolumn w tabelach bazy danych, które zawierają dane plików i rejestru.  
  
## <a name="database-entries"></a>Wpisy w bazie danych  
 Do zainstalowania pakietu VSPackage, to pakiet Instalatora Windows musi zawierać wpisy w bazie danych można wykonywać następujące zadania:  
  
- Wyszukaj systemu, aby zlokalizować wersje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Twojego pakietu VSPackage obsługuje (przy użyciu tabel Instalatora Windows, które zawierają AppSearch powoduje niepoprawne obcięcie CompLocator, RegLocator, DrLocator i podpis).  
  
- Anuluj instalację, jeśli nie obsługiwaną wersję [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest zainstalowany lub jeśli wymagania systemu innego pakietu VSPackage nie jest spełniony (przy użyciu tabeli LaunchCondition).  
  
- Instalowanie pakietu VSPackage i pliki zależne (przy użyciu katalogu, składników i tabele plików).  
  
- Dodaj odpowiednie informacje dotyczące pakietu VSPackage (przy użyciu tabeli w rejestrze).  
  
- Integrowanie pakietu VSPackage w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] przez wywołanie metody **/Setup devenv.exe** (przy użyciu tabeli Akcja niestandardowa).  
  
  Aby uzyskać więcej informacji, zobacz [Instalatora Windows](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Konfigurowanie narzędzia  
 Szeroką gamą narzędzi innych firm Instalatora zapewniają środowisko projektowe dla pakietów Instalatora Windows. Dwa bezpłatne narzędzia są następujące:  
  
- InstallShield Limited Edition  
  
   Ograniczona wersja programu InstallShield można uzyskać za pomocą programu Visual Studio **nowy projekt** okna dialogowego. Rozwiń **inne typy projektów** , a następnie wybierz **instalacja i wdrożenie**. Wybierz szablon InstallShield.  
  
- Zestaw narzędzi XML Instalatora Windows  
  
   Zestaw narzędzi kompilacji pakietów Instalatora Windows przy użyciu plików źródłowych XML. Zestaw narzędzi to projekt typu open source firmy Microsoft. Możesz pobrać kod źródłowy i pliki wykonywalne z [ http://sourceforge.net/projects/wix ](http://sourceforge.net/projects/wix).  
  
  Komercyjne produktów, które integrują [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] przy użyciu [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], zobacz [ http://visualstudiogallery.com ](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Zobacz też  
 [Instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
