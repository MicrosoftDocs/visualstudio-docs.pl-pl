---
title: Podtypy projektu | Microsoft Docs
description: Dowiedz się, jak podtypy projektów pozwalają dostosować zachowanie systemów projektu programu Visual Studio. Pakietów VSPackage Implementuj podtypy projektu przy użyciu agregacji COM.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 05240ee72aef85e50d07c7a39df1c819f04933a2
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876302"
---
# <a name="project-subtypes"></a>Podtypy projektów
Podtypy projektu pozwalają dostosować lub określić zachowanie systemów projektowych programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Dostosowania obejmują zapisywanie dodatkowych danych w pliku projektu, Dodawanie lub Filtrowanie elementów w oknie dialogowym **Dodaj nowy element** , kontrolowanie sposobu debugowania i wdrażania zestawów oraz rozszerzanie okna dialogowego **strony właściwości** projektu. Pakietów VSPackage Implementuj podtypy projektu przy użyciu agregacji COM.

> [!NOTE]
> System projektu Visual C++ nie obsługuje podtypów projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sam używa podtypów projektu do implementowania SQL Server i inteligentnych projektów urządzeń.

## <a name="in-this-section"></a>W tej sekcji

- [Projektowanie podtypów projektów](../../extensibility/internals/project-subtypes-design.md)

  Opisuje koncepcję podtypów projektu.

- [Sekwencja inicjowania podtypów projektów](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

  Opisuje sekwencję inicjowania podtypu projektu programistycznego według [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska.

- [Właściwości i metody rozszerzane przez podtypy projektów](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

  Zawiera szczegółowe opisy funkcji i metod, które są najczęściej rozszerzane przy użyciu podtypów projektu.

- [Utrwalanie danych w pliku projektu programu MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

  Opisuje, jak utrwalać dane w pliku projektu i jak używać <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> do przechowywania danych w pliku projektu na poziomach agregacji podtypów projektu.

- [Interfejs użytkownika właściwości projektu](../../extensibility/internals/project-property-user-interface.md)

  Opisuje, w jaki sposób podtypy projektu mogą modyfikować okno dialogowe **strony właściwości** projektu.

- [Rozszerzanie modelu obiektu projektu podstawowego](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

  Zawiera informacje dotyczące sposobu, w jaki podtypy projektu mogą używać rozszerzeń automatyzacji do rozbudowania modelu obiektów automatyzacji.

- [Dodawanie elementów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

  Opisuje sposób dodawania elementów do okna dialogowego **Dodaj nowy element** .

- [Zapisywanie danych w plikach projektu](../../extensibility/saving-data-in-project-files.md)

  Wyjaśnia, w jaki sposób podtyp projektu może zapisywać i pobierać dane specyficzne dla określonego typu w pliku projektu przy użyciu struktury pakietu zarządzanego (MPF).

- [Obsługa wdrożeń specjalistycznych](../../extensibility/internals/handling-specialized-deployment.md)

  Wyjaśnia, w jaki sposób podtypy projektu mogą dostarczać wyspecjalizowane zachowanie wdrażania przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfejsu.

- [Dodawanie i usuwanie stron właściwości](../../extensibility/adding-and-removing-property-pages.md)

  Opisuje Dodawanie i usuwanie stron właściwości w projektancie projektu.

## <a name="related-sections"></a>Sekcje pokrewne

- [Typy projektów](../../extensibility/internals/project-types.md)

  Zawiera łącza do tematów zawierających szczegółowe informacje o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektach.
