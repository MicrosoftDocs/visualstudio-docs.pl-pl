---
title: Co &apos; nowego w zestawie SDK Visual Studio 2017 | Microsoft Docs
description: Zestaw VISUAL STUDIO SDK zawiera nowe i zaktualizowane funkcje dla wersji Visual Studio 2017, w tym zaktualizowany format VSIX w wersji 3.
ms.custom: SEO-VS-2020
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0b0b7852fa7e20f4ee6951e57c5c19f4b5454028
ms.sourcegitcommit: 3c6c263a1c0b20f084290ce45295a46027da33b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2021
ms.locfileid: "113756897"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Co&#39;nowego w zestawie SDK Visual Studio 2017

Zestaw Visual Studio SDK zawiera następujące nowe i zaktualizowane funkcje w wersji Visual Studio 2017.

## <a name="vsix-v3-format"></a>Format VSIX v3

W celu obsługi nowej lekkiej instalacji programu Visual Studio 2017 format manifestu rozszerzenia VSIX został zaktualizowany do wersji 3 (VSIX v3).

Nowy format obsługuje:

* Jawne deklarowanie wymagań wstępnych, które mają być wykrywane i instalowane przez program VSIXInstaller.
* Zestawy Ngen podczas instalacji rozszerzenia.
* Instalowanie zasobów poza zwykłym głównym rozszerzeniem.

Aby dowiedzieć się więcej o tych zmianach, zobacz następujące tematy:

* [Zmiany rozszerzalności w Visual Studio 2017 r.](breaking-changes-2017.md)
* [Obsługa Ngen w rozszerzeniu VSIX v3](ngen-support.md)
* [Instalowanie poza folderem rozszerzeń](set-install-root.md)
* [Często zadawane pytania dotyczące rozszerzalności Visual Studio 2017](faq-2017.yml)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migrowanie projektu rozszerzalności do Visual Studio 2017 r.

Aby dowiedzieć się, jak zaktualizować projekty rozszerzalności i ich manifesty VSIX do programu Visual Studio 2017, zobacz Temat How [to: Migrate extensibility projects to Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)(Jak migrować projekty rozszerzalności do programu Visual Studio 2017).

## <a name="custom-project-and-item-templates"></a>Niestandardowe szablony projektów i elementów

Począwszy od Visual Studio 2017 r., skanowanie w celu skanowania niestandardowych szablonów projektów i elementów nie będzie już wykonywane. Zamiast tego rozszerzenie musi dostarczać pliki manifestu szablonu, które opisują lokalizację instalacji tych szablonów. Rozszerzenia VSIX Visual Studio 2017 można zaktualizować za pomocą programu . W przypadku wdrażania rozszerzenia przy użyciu pliku MSI należy ręcznie wygenerować pliki manifestu szablonu. Aby uzyskać więcej informacji, zobacz Upgrade custom project and item templates for Visual Studio 2017 (Uaktualnianie niestandardowych szablonów projektów i elementów [dla programu Visual Studio 2017).](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md) Schemat manifestu szablonu jest udokumentowany w Visual Studio [manifestu szablonu](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Zaktualizowane wytyczne dotyczące wydajności rozszerzeń

W obszarze Zarządzanie [pakietami](how-to-diagnose-extension-performance.md) [VSPackage](managing-vspackages.md) znajduje się nowy artykuł Jak diagnozować wydajność rozszerzenia, aby pokazać, jak wykrywać i analizować wpływ rozszerzenia na czas uruchamiania Visual Studio ładowania rozwiązań.
