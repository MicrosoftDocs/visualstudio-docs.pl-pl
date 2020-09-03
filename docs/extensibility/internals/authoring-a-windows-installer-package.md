---
title: Tworzenie pakietu Instalator Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d30c0e2b3b375e6e0efedddd3a017fbfb8646a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710036"
---
# <a name="author-a-windows-installer-package"></a>Tworzenie pakietu Instalator Windows
Dane są dyskami Instalator Windows modelem. Zamiast pisać skrypt proceduralny do kopiowania plików i zapisywania wpisów rejestru, na przykład w tabelach bazy danych można tworzyć wiersze i kolumny zawierające dane plików i rejestru.

## <a name="database-entries"></a>Wpisy bazy danych
Aby zainstalować pakietu VSPackage, pakiet Instalator Windows musi zawierać wpisy bazy danych, aby wykonać następujące zadania:

- Przeszukaj system, aby zlokalizować wersje programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pakietu VSPackage (przy użyciu tabel Instalator Windows zawierających AppSearch, CompLocator, RegLocator, DrLocator i Signature).

- Jeśli nie zainstalowano żadnej obsługiwanej wersji programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lub nie jest spełnione inne wymaganie systemowe pakietu VSPackage (za pomocą tabeli LaunchCondition), Anuluj instalację.

- Zainstaluj pliki pakietu VSPackage i zależne (przy użyciu katalogu, składnika i tabel plików).

- Dodaj odpowiednie informacje dotyczące pakietu VSPackage do rejestru (przy użyciu tabeli rejestru).

- Zintegruj pakietu VSPackage w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , wywołując **devenv.exe/Setup** (przy użyciu tabeli GetProcAddress).

Aby uzyskać więcej informacji, zobacz [Instalator Windows](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Narzędzia Instalatora
Różne narzędzia Instalatora innych firm zapewniają środowisko programistyczne dla pakietów Instalator Windows. Dostępne są następujące bezpłatne narzędzia:

- InstallShield Limited Edition

   Ograniczoną wersję programu InstallShield można uzyskać za pomocą okna dialogowego **Nowy projekt** programu Visual Studio. Rozwiń węzeł **Inne typy projektów** , a następnie wybierz pozycję **Instalacja i wdrożenie**. Wybierz szablon InstallShield.

- Zestaw narzędzi Instalator Windows XML

   Zestaw narzędzi Instalator Windows XML (WiX) kompiluje Instalator Windows pakiety ze źródłowych plików XML. Zestaw narzędzi WiX jest projektem typu open source firmy Microsoft. Możesz pobrać kod źródłowy i pliki wykonywalne z zestawu [narzędzi WIX](https://sourceforge.net/projects/wix/).

   Aby uzyskać komercyjne produkty, które integrują się z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usługą [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , zobacz [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Zobacz też
- [Zainstaluj pakietów VSPackage z Instalator Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
