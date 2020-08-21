---
title: Co &apos; nowego w zestawie SDK programu Visual Studio 2017 | Microsoft Docs
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fb5b81341f8184d713755b3b934fbae4c8031b1
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2020
ms.locfileid: "88711602"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Co nowego w&#39;s w zestawie SDK programu Visual Studio 2017

Zestaw Visual Studio SDK zawiera następujące nowe i zaktualizowane funkcje programu Visual Studio 2017.

## <a name="vsix-v3-format"></a>Format VSIX v3

Aby zapewnić obsługę nowej instalacji lekkiej programu Visual Studio 2017, format manifestu rozszerzenia VSIX został zaktualizowany do wersji 3 (VSIX v3).

Nowy format obsługuje:

* Jawne deklarowanie wymagań wstępnych, które mają być wykrywane i instalowane przez Instalator VSIX.
* Zestawy NGen podczas instalacji rozszerzenia.
* Instalowanie zasobów poza zwykłym katalogiem głównym rozszerzenia.

Aby dowiedzieć się więcej o tych zmianach, zobacz następujące tematy:

* [Zmiany rozszerzalności dla programu Visual Studio 2017](breaking-changes-2017.md)
* [Obsługa Ngen w rozszerzeniu VSIX v3](ngen-support.md)
* [Instalowanie poza folderem rozszerzeń](set-install-root.md)
* [Często zadawane pytania dotyczące rozszerzalności programu Visual Studio 2017](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migrowanie projektu rozszerzalności do programu Visual Studio 2017

Aby dowiedzieć się, jak zaktualizować swoje projekty rozszerzalności i ich manifesty VSIX do programu Visual Studio 2017, zobacz [How to: Migrowanie projektów rozszerzalności do programu Visual studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Niestandardowe szablony projektów i elementów

Począwszy od programu Visual Studio 2017, skanowanie w poszukiwaniu niestandardowych szablonów projektów i elementów nie będzie już wykonywane. Zamiast tego rozszerzenie musi dostarczyć pliki manifestu szablonu opisujące lokalizację instalacji tych szablonów. Aby zaktualizować rozszerzenia VSIX, można użyć programu Visual Studio 2017. W przypadku wdrożenia rozszerzenia przy użyciu pliku MSI musisz ręcznie wygenerować pliki manifestu szablonu. Aby uzyskać więcej informacji, zobacz [uaktualnianie niestandardowych szablonów projektów i elementów dla programu Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schemat manifestu szablonu jest udokumentowany w [dokumentacji schematu manifestu szablonu programu Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Zaktualizowane wskazówki dotyczące wydajności rozszerzenia

Istnieje nowa [procedura: diagnozowanie](how-to-diagnose-extension-performance.md) artykułu dotyczącego wydajności rozszerzeń w obszarze [Zarządzanie pakietów VSPackage](managing-vspackages.md) , aby pokazać, jak wykrywać i analizować wpływ rozszerzeń na czas uruchamiania i ładowania rozwiązań w programie Visual Studio.
