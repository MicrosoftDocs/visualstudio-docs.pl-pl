---
title: Tworzenie pakietu Instalatora Windows | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93c69b2fba2bc866673b294a4f5c975a6ce3eb6a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020951"
---
# <a name="author-a-windows-installer-package"></a>Tworzenie pakietu Instalatora Windows
Danych zależy od modelu Instalatora Windows. Zamiast pisania procedurach skryptu, aby skopiować pliki i Zapisz wpisy rejestru, na przykład, możesz tworzyć wierszy i kolumn w tabelach bazy danych, które zawierają dane plików i rejestru.  
  
## <a name="database-entries"></a>Wpisy w bazie danych  
Do zainstalowania pakietu VSPackage, to pakiet Instalatora Windows musi zawierać wpisy w bazie danych można wykonywać następujące zadania:  
  
- Wyszukaj systemu, aby zlokalizować wersje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Twojego pakietu VSPackage obsługuje (przy użyciu tabel Instalatora Windows, które zawierają AppSearch powoduje niepoprawne obcięcie CompLocator, RegLocator, DrLocator i podpis).  
  
- Anuluj instalację, jeśli nie obsługiwaną wersję [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest zainstalowany lub jeśli wymagania systemu innego pakietu VSPackage nie jest spełniony (przy użyciu tabeli LaunchCondition).  
  
- Instalowanie pakietu VSPackage i pliki zależne (przy użyciu katalogu, składników i tabele plików).  
  
- Dodaj odpowiednie informacje dotyczące pakietu VSPackage (przy użyciu tabeli w rejestrze).  
  
- Integrowanie pakietu VSPackage w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przez wywołanie metody **/Setup devenv.exe** (przy użyciu tabeli Akcja niestandardowa).  
  
Aby uzyskać więcej informacji, zobacz [Instalatora Windows](/windows/desktop/Msi/windows-installer-portal).
  
## <a name="setup-tools"></a>Konfigurowanie narzędzia  
Szeroką gamą narzędzi innych firm Instalatora zapewniają środowisko projektowe dla pakietów Instalatora Windows. Dostępne są następujące narzędzia wolne:  
  
- Programu InstallShield limited edition  
  
   Ograniczona wersja programu InstallShield można uzyskać za pomocą programu Visual Studio **nowy projekt** okna dialogowego. Rozwiń **inne typy projektów** , a następnie wybierz **instalacja i wdrożenie**. Wybierz szablon InstallShield.  
  
- Zestaw narzędzi XML Instalatora Windows  
  
   Zestaw narzędzi XML Instalatora Windows (WiX) tworzy pakiety Instalatora Windows przy użyciu plików źródłowych XML. Zestaw narzędzi WiX to projekt typu open source firmy Microsoft. Możesz pobrać kod źródłowy i pliki wykonywalne z [zestaw narzędzi Wix](http://sourceforge.net/projects/wix).  
  
   Komercyjne produktów, które integrują [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przy użyciu [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], zobacz [ http://visualstudiogallery.com ](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Zobacz także  
 [Instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)