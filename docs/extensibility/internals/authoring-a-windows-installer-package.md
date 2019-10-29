---
title: Tworzenie pakietu Instalator Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa967b5f23ff9f4e5afa67b9b1cb4e83707616c6
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982233"
---
# <a name="author-a-windows-installer-package"></a>Tworzenie pakietu Instalator Windows
Dane są dyskami Instalator Windows modelem. Zamiast pisać skrypt proceduralny do kopiowania plików i zapisywania wpisów rejestru, na przykład w tabelach bazy danych można tworzyć wiersze i kolumny zawierające dane plików i rejestru.

## <a name="database-entries"></a>Wpisy bazy danych
Aby zainstalować pakietu VSPackage, pakiet Instalator Windows musi zawierać wpisy bazy danych, aby wykonać następujące zadania:

- Przeszukaj system, aby zlokalizować wersje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługiwane przez pakietu VSPackage (przy użyciu tabel Instalator Windows, które zawierają AppSearch, CompLocator, RegLocator, DrLocator i Signature).

- Anuluj instalację, jeśli nie jest zainstalowana żadna obsługiwana wersja programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lub jeśli nie jest spełnione inne wymaganie systemowe pakietu VSPackage (za pomocą tabeli LaunchCondition).

- Zainstaluj pliki pakietu VSPackage i zależne (przy użyciu katalogu, składnika i tabel plików).

- Dodaj odpowiednie informacje dotyczące pakietu VSPackage do rejestru (przy użyciu tabeli rejestru).

- Zintegruj pakietu VSPackage w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], wywołując **devenv. exe/setup** (za pomocą tabeli GetProcAddress).

Aby uzyskać więcej informacji, zobacz [Instalator Windows](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Narzędzia Instalatora
Różne narzędzia Instalatora innych firm zapewniają środowisko programistyczne dla pakietów Instalator Windows. Dostępne są następujące bezpłatne narzędzia:

- InstallShield Limited Edition

   Ograniczoną wersję programu InstallShield można uzyskać za pomocą okna dialogowego **Nowy projekt** programu Visual Studio. Rozwiń węzeł **Inne typy projektów** , a następnie wybierz pozycję **Instalacja i wdrożenie**. Wybierz szablon InstallShield.

- Zestaw narzędzi Instalator Windows XML

   Zestaw narzędzi Instalator Windows XML (WiX) kompiluje Instalator Windows pakiety ze źródłowych plików XML. Zestaw narzędzi WiX jest projektem typu open source firmy Microsoft. Możesz pobrać kod źródłowy i pliki wykonywalne z zestawu [narzędzi WIX](https://sourceforge.net/projects/wix/).

   W przypadku produktów komercyjnych, które integrują się z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przy użyciu [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], zobacz [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Zobacz także
- [Zainstaluj pakietów VSPackage z Instalator Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)