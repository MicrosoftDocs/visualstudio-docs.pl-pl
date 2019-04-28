---
title: Podtypy projektów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 73cf7fe43dcbe15bdeedf6822c9172533e6d420b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63423066"
---
# <a name="project-subtypes"></a>Podtypy projektów
Podtypy projektów pozwalają dostosować lub flavor zachowanie systemów projektu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Możliwe modyfikacje obejmują zapisywanie dodatkowe dane w pliku projektu, dodawanie lub filtrowanie elementów w **Dodaj nowy element** okno dialogowe, kontrolowanie jak debugować zestawy i wdrożona i rozszerzanie projektu **właściwości Strony** okno dialogowe. Pakietów VSPackage zaimplementować podtypy projektów za pomocą modelu COM agregacji.

> [!NOTE]
> System projektów języka Visual C++ nie obsługuje podtypy projektów. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podtypy projektów sam używa do implementacji projektów programu SQL Server i urządzenia przenośne.

## <a name="in-this-section"></a>W tej sekcji
- [Projektowanie podtypów projektów](../../extensibility/internals/project-subtypes-design.md)

 Omówienie pojęć dotyczących podtypy projektów.

- [Sekwencja inicjowania podtypów projektów](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

 Zawiera opis sekwencji inicjowania podtypu projektu programowe przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska.

- [Właściwości i metody rozszerzane przez podtypy projektów](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

 Zawiera szczegółowe opisy funkcji i metod najczęściej rozszerzyć za pomocą podtypy projektów.

- [Utrwalanie danych w pliku projektu programu MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

 Opisuje sposoby utrwalania danych w pliku projektu i sposobu użycia <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> do obsługi danych w pliku projektu na poziomach agregacji podtypu projektu.

- [Interfejs użytkownika właściwości projektu](../../extensibility/internals/project-property-user-interface.md)

 W tym artykule opisano, jak podtypy projektów można zmodyfikować projekt **stron właściwości** okno dialogowe.

- [Rozszerzanie modelu obiektu projektu podstawowego](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

 Zawiera informacje dotyczące sposobu podtypy projektów umożliwia automatyzacji urządzeń Extender Rozszerzanie modelu obiektu automatyzacji.

- [Dodawanie elementów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

 W tym artykule opisano sposób dodawania elementów do **Dodaj nowy element** okno dialogowe.

- [Zapisywanie danych w plikach projektu](../../extensibility/saving-data-in-project-files.md)

 Wyjaśnia, jak podtypu projektu można zapisywać i pobierać dane specyficzne dla podtypu w pliku projektu przy użyciu Framework pakietu zarządzanego (MPF).

- [Obsługa wdrożeń specjalistycznych](../../extensibility/internals/handling-specialized-deployment.md)

 Wyjaśnia, jak podtypy projektów można podać sposób działania wdrożenia specjalistycznych implementując <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfejsu.

- [Dodawanie i usuwanie stron właściwości](../../extensibility/adding-and-removing-property-pages.md)

 W tym artykule opisano Dodawanie i usuwanie stron właściwości w Projektancie projektu.

## <a name="related-sections"></a>Sekcje pokrewne
- [Typy projektów](../../extensibility/internals/project-types.md)

 Zawiera łącza do tematów, ze szczegółami dotyczącymi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektów.