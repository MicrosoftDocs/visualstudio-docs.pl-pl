---
title: Co&#39;nowości w SDK programu Visual Studio 2017 | Dokumenty firmy Microsoft
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88330aa68f2a3752431fd2fbe6c5c1c649acbb8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697209"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Co&#39;nowego w SDK programu Visual Studio 2017

Visual Studio SDK ma następujące nowe i zaktualizowane funkcje programu Visual Studio 2017.

## <a name="vsix-v3-format"></a>Format VSIX v3

Aby obsługiwać nową lekką instalację programu Visual Studio 2017, format manifestu rozszerzenia VSIX został zaktualizowany do wersji 3 (VSIX v3).

Nowy format obsługuje:

* Jawnie deklarując wymagania wstępne, które mają być wykryte i zainstalowane przez VSIXInstaller.
* zespołów Ngen przy instalacji rozszerzeń.
* Instalowanie zasobów poza zwykłym katalogiem głównym rozszerzeń.

Aby dowiedzieć się więcej o tych zmianach, zobacz następujące tematy:

* [Zmiany rozszerzalności programu Visual Studio 2017](breaking-changes-2017.md)
* [Obsługa Ngen w rozszerzeniu VSIX v3](ngen-support.md)
* [Instalowanie poza folderem rozszerzeń](set-install-root.md)
* [Często zadawane pytania dotyczące rozszerzalności programu Visual Studio 2017](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migrowanie projektu rozszerzalności do programu Visual Studio 2017

Aby dowiedzieć się, jak zaktualizować projekty rozszerzalności i ich manifesty VSIX do programu Visual Studio 2017, zobacz [Jak: Migrowanie projektów rozszerzalności do programu Visual Studio 2017.](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)

## <a name="custom-project-and-item-templates"></a>Niestandardowe szablony projektów i elementów

Począwszy od programu Visual Studio 2017 skanowanie w poszukiwaniu szablonów niestandardowych projektów i elementów nie będzie już wykonywane. Zamiast tego rozszerzenie musi zawierać pliki manifestu szablonu, które opisują lokalizację instalacji tych szablonów. Za pomocą programu Visual Studio 2017 można zaktualizować rozszerzenia VSIX. Jeśli rozmieszczenia rozszerzenia przy użyciu MSI, należy wygenerować pliki manifestu szablonu ręcznie. Aby uzyskać więcej informacji, zobacz [Uaktualnianie szablonów niestandardowych projektów i elementów dla programu Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schemat manifestu szablonu jest udokumentowany w [odwołaniu do schematu manifestu szablonu programu Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Zaktualizowane wskazówki dotyczące wydajności rozszerzenia

Istnieje nowy [sposób: Diagnozowanie wydajności rozszerzenia](how-to-diagnose-extension-performance.md) artykuł w obszarze [Zarządzanie pakietami VSPackages,](managing-vspackages.md) aby pokazać, jak wykryć i analizować wpływ rozszerzenia na czas uruchamiania i ładowania rozwiązania programu Visual Studio.
