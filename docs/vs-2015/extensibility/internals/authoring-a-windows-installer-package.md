---
title: Tworzenie pakietu Instalator Windows | Microsoft Docs
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
ms.openlocfilehash: 58529dabbb52ceb751c67be24beb1d21285a1de6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74301129"
---
# <a name="authoring-a-windows-installer-package"></a>Tworzenie pakietu Instalatora Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dane są dyskami Instalator Windows modelem. Zamiast pisać skrypt proceduralny do kopiowania plików i zapisywania wpisów rejestru, na przykład w tabelach bazy danych można tworzyć wiersze i kolumny zawierające dane plików i rejestru.  
  
## <a name="database-entries"></a>Wpisy bazy danych  
 Aby zainstalować pakietu VSPackage, pakiet Instalator Windows musi zawierać wpisy bazy danych, aby wykonać następujące zadania:  
  
- Przeszukaj system, aby zlokalizować wersje programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pakietu VSPackage (przy użyciu tabel Instalator Windows zawierających AppSearch, CompLocator, RegLocator, DrLocator i Signature).  
  
- Jeśli nie zainstalowano żadnej obsługiwanej wersji programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] lub nie jest spełnione inne wymaganie systemowe pakietu VSPackage (za pomocą tabeli LaunchCondition), Anuluj instalację.  
  
- Zainstaluj pliki pakietu VSPackage i zależne (przy użyciu katalogu, składnika i tabel plików).  
  
- Dodaj odpowiednie informacje dotyczące pakietu VSPackage do rejestru (przy użyciu tabeli rejestru).  
  
- Zintegruj pakietu VSPackage w programie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , wywołując **devenv.exe/Setup** (przy użyciu tabeli GetProcAddress).  
  
  Aby uzyskać więcej informacji, zobacz [Instalator Windows](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Narzędzia Instalatora  
 Różne narzędzia Instalatora innych firm zapewniają środowisko programistyczne dla pakietów Instalator Windows. Poniżej przedstawiono dwa bezpłatne narzędzia:  
  
- InstallShield Limited Edition  
  
   Ograniczoną wersję programu InstallShield można uzyskać za pomocą okna dialogowego **Nowy projekt** programu Visual Studio. Rozwiń węzeł **Inne typy projektów** , a następnie wybierz pozycję **Instalacja i wdrożenie**. Wybierz szablon InstallShield.  
  
- Zestaw narzędzi XML Instalatora Windows  
  
   Zestaw narzędzi kompiluje pakiety Instalator Windows ze źródłowych plików XML. Zestaw narzędzi jest projektem typu open source firmy Microsoft. Kod źródłowy i pliki wykonywalne można pobrać z programu [http://sourceforge.net/projects/wix](https://sourceforge.net/projects/wix/) .  
  
  Aby uzyskać komercyjne produkty, które integrują się z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usługą [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , zobacz [https://marketplace.visualstudio.com/](https://marketplace.visualstudio.com/) .  
  
## <a name="see-also"></a>Zobacz też  
 [Instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
