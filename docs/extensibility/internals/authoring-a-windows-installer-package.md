---
title: Tworzenie pakietu Instalatora Windows | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710036"
---
# <a name="author-a-windows-installer-package"></a>Tworzenie pakietu Instalatora Windows
Dane napędzają model Instalatora Windows. Zamiast pisać skrypt proceduralny do kopiowania plików i pisania wpisów rejestru, na przykład można tworzyć wiersze i kolumny w tabelach bazy danych, które zawierają dane pliku i rejestru.

## <a name="database-entries"></a>Wpisy bazy danych
Aby zainstalować pakiet VSPackage, pakiet Instalatora Windows musi zawierać wpisy bazy danych w celu wykonania następujących zadań:

- Przeszukaj system, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zlokalizować wersje swoich platform VSPackage (przy użyciu tabel Instalatora Windows, które zawierają AppSearch, CompLocator, RegLocator, DrLocator i Signature).

- Anuluj instalację, jeśli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie jest zainstalowana żadna obsługiwana wersja lub jeśli nie jest spełnione inne wymagania systemowe programu VSPackage (przy użyciu tabeli LaunchCondition).

- Zainstaluj pliki VSPackage i zależne (przy użyciu katalogu, składnika i tabel plików).

- Dodaj odpowiednie informacje dla VSPackage do rejestru (przy użyciu tabeli Rejestru).

- Zintegruj vspackage przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wywołanie **devenv.exe /setup** (przy użyciu tabeli CustomAction).

Aby uzyskać więcej informacji, zobacz [Instalator Windows](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Narzędzia do instalacji
Różne narzędzia do konfiguracji innych firm zapewniają środowisko programistyczne dla pakietów Instalatora Windows. Dostępne są następujące bezpłatne narzędzia:

- Edycja limitowana InstallShield

   Można uzyskać ograniczoną wersję InstallShield za pośrednictwem okna dialogowego Visual Studio **Nowy projekt.** Rozwiń **węzeł Inne typy projektów,** a następnie wybierz pozycję **Ustawienia i wdrożenie**. Wybierz szablon InstallShield.

- Zestaw narzędzi XML Instalatora Windows

   Zestaw narzędzi XML Instalatora Windows (WiX) tworzy pakiety Instalatora Windows z plików źródłowych XML. Zestaw narzędzi WiX jest projektem open source firmy Microsoft. Możesz pobrać kod źródłowy i pliki wykonywalne z [zestawu narzędzi Wix](https://sourceforge.net/projects/wix/).

   W przypadku produktów [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komercyjnych, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]które integrują się przy użyciu programu [Visual Studio Marketplace.](https://marketplace.visualstudio.com/)

## <a name="see-also"></a>Zobacz też
- [Instalowanie pakietów VSPackages z Instalatorem Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
