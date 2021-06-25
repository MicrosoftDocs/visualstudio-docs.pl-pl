---
title: Typy podtypów | Microsoft Docs
description: Dowiedz się, jak podtypy projektów umożliwiają dostosowywanie zachowania systemów projektu Visual Studio. Pakiet VSPackages implementuje podtypy projektów przy użyciu agregacji COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cd0f959d300fdc797d9e42d581a163b8b0892591
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903596"
---
# <a name="project-subtypes"></a>Podtypy projektów
Podtypy projektu umożliwiają dostosowanie lub dopasowanie zachowania systemów projektu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Dostosowania obejmują zapisywanie dodatkowych danych w pliku projektu, dodawanie  lub filtrowanie elementów w oknie dialogowym Dodawanie nowego elementu, kontrolowanie sposobu debugowania i wdrażania zestawów oraz rozszerzanie okna dialogowego **Strony** właściwości projektu. Pakiet VSPackages implementuje podtypy projektów przy użyciu agregacji COM.

> [!NOTE]
> System Visual C++ projektu nie obsługuje podtypów projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sama używa podtypów projektu do implement SQL Server i projektów urządzeń inteligentnych.

## <a name="in-this-section"></a>W tej sekcji

- [Projektowanie podtypów projektów](../../extensibility/internals/project-subtypes-design.md)

  Opisuje koncepcję podtypów projektów.

- [Sekwencja inicjowania podtypów projektów](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

  Opisuje sekwencję inicjowania podtypu projektu programowego według [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska.

- [Właściwości i metody rozszerzane przez podtypy projektów](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

  Zawiera szczegółowe opisy funkcji i metod, które są najczęściej rozszerzane przy użyciu podtypów projektu.

- [Utrwalanie danych w pliku projektu programu MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

  Opisuje sposób utrwalania danych w pliku projektu i sposób użycia do obsługi danych w pliku projektu na różnych poziomach <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> agregacji podtypu projektu.

- [Interfejs użytkownika właściwości projektu](../../extensibility/internals/project-property-user-interface.md)

  Opisuje, jak podtypy projektów mogą modyfikować okno dialogowe **Strony właściwości** projektu.

- [Rozszerzanie modelu obiektu projektu podstawowego](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

  Zawiera informacje na temat sposobu, w jaki podtypy projektów mogą używać rozszerzenia automatyzacji do rozszerzania modelu obiektów automatyzacji.

- [Dodawanie elementów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

  Opisuje sposób dodawania elementów do **okna dialogowego Dodawanie** nowego elementu.

- [Zapisywanie danych w plikach projektu](../../extensibility/saving-data-in-project-files.md)

  Wyjaśnia, jak podtyp projektu może zapisywać i pobierać dane specyficzne dla podtypu w pliku projektu przy użyciu struktury pakietów zarządzanych (MPF).

- [Obsługa wdrożeń specjalistycznych](../../extensibility/internals/handling-specialized-deployment.md)

  Wyjaśnia, w jaki sposób podtypy projektów mogą dostarczać wyspecjalizowane zachowanie wdrażania przez zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfejsu.

- [Dodawanie i usuwanie stron właściwości](../../extensibility/adding-and-removing-property-pages.md)

  Opisuje dodawanie i usuwanie stron właściwości w projektancie projektów.

## <a name="related-sections"></a>Sekcje pokrewne

- [Typy projektów](../../extensibility/internals/project-types.md)

  Zawiera linki do tematów szczegółowo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] opisjących projekty.
