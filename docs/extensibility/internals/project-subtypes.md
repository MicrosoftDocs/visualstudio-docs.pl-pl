---
title: Podtypy projektu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71dab4767c806b44cbd1f9638738b4a13d6b2bcb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706411"
---
# <a name="project-subtypes"></a>Podtypy projektów
Podtypy projektu umożliwiają dostosowanie lub smak zachowania systemów [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]projektu . Dostosowania obejmują zapisywanie dodatkowych danych w pliku projektu, dodawanie lub filtrowanie elementów w oknie dialogowym **Dodawanie nowego elementu,** kontrolowanie sposobu debugowania i wdrażania zestawów oraz rozszerzanie okna dialogowego **Strony właściwości** projektu. VSPackages implementują podtypy projektu przy użyciu agregacji COM.

> [!NOTE]
> System projektu Visual C++ nie obsługuje podtypów projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]sama używa podtypów projektu do implementowania projektów programu SQL Server i smart device.

## <a name="in-this-section"></a>W tej sekcji
- [Projektowanie podtypów projektów](../../extensibility/internals/project-subtypes-design.md)

 Opisuje pojęcie podtypów projektu.

- [Sekwencja inicjowania podtypów projektów](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

 Opisuje sekwencję inicjowania podtypu projektu programowego według [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska.

- [Właściwości i metody rozszerzane przez podtypy projektów](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

 Zawiera szczegółowe opisy funkcji i metod najczęściej rozszerzane przy użyciu podtypów projektu.

- [Utrwalanie danych w pliku projektu programu MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

 W tym artykule opisano sposób utrwalania <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> danych w pliku projektu i sposobu używania do obsługi danych w pliku projektu na poziomach agregacji podtypu projektu.

- [Interfejs użytkownika właściwości projektu](../../extensibility/internals/project-property-user-interface.md)

 W tym artykule opisano, jak podtypy projektu mogą modyfikować okno dialogowe **Strony właściwości** projektu.

- [Rozszerzanie modelu obiektu projektu podstawowego](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

 Zawiera informacje o tym, jak podtypy projektu można użyć rozszerzenia automatyzacji, aby rozszerzyć model obiektów automatyzacji.

- [Dodawanie elementów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

 W tym artykule opisano sposób dodawania elementów do okna dialogowego **Dodawanie nowego elementu.**

- [Zapisywanie danych w plikach projektu](../../extensibility/saving-data-in-project-files.md)

 W tym artykule wyjaśniono, jak podtyp projektu może zapisywać i pobierać dane specyficzne dla podtypu w pliku projektu przy użyciu struktury pakietu zarządzanego (MPF).

- [Obsługa wdrożeń specjalistycznych](../../extensibility/internals/handling-specialized-deployment.md)

 W tym artykule wyjaśniono, jak podtypy projektu mogą dostarczać zachowania wdrożenia specjalistycznego, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> implementując interfejs.

- [Dodawanie i usuwanie stron właściwości](../../extensibility/adding-and-removing-property-pages.md)

 Opisuje dodawanie i usuwanie stron właściwości w projektancie projektu.

## <a name="related-sections"></a>Sekcje pokrewne
- [Project Types (Typy projektów)](../../extensibility/internals/project-types.md)

 Zawiera łącza do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tematów przedstawiających szczegółowe informacje o projektach.
