---
title: Rozszerzanie projektów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0333e09aee207e10657999dda4b5b1d59e181cf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341109"
---
# <a name="extend-projects"></a>Rozszerzanie projektów
Projekty i rozwiązania są sposoby programu Visual Studio organizuje plików kodu i zasobów w jednostki kompilacji i wdrożenia. Można znaleźć więcej informacji na temat projektów w [projektów (Visual Studio SDK)](../extensibility/extending-projects.md).

 Można utworzyć własne typy projektów za pomocą programu Visual Studio SDK i środowiska pakietu zarządzanego dla projektów, które można pobrać w [zarządzanego środowiska pakietu dla projektów](https://github.com/tunnelvisionlabs/MPFProj10). Aby zrozumieć, jak niestandardowe projekty są wdrażane, zobacz [Generowanie nowego projektu: Za kulisami, część jednego](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) i [Generowanie nowego projektu: Za kulisami, część dwóch](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Tematy w tej sekcji opisano sposób tworzenia projektów niestandardowych i jak zarządzać różnego rodzaju rozwiązania Visual Studio.

## <a name="in-this-section"></a>W tej sekcji
- [Tworzenie systemu podstawowego projektu, część 1](../extensibility/creating-a-basic-project-system-part-1.md) w tym artykule opisano sposób tworzenia systemu niestandardowego projektu.

- [Tworzenie systemu podstawowego projektu, część 2](../extensibility/creating-a-basic-project-system-part-2.md) w tym artykule opisano sposób tworzenia systemu niestandardowego projektu.

- [Zapisywanie danych w plikach projektu](../extensibility/saving-data-in-project-files.md) Explains, jak dodać do projektu (<em>.</em> Proj *), pliki.

- [Sprawdź podtypów projektu w czasie wykonywania](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) wyjaśnia, jak sprawdzić podtypu projektu w czasie wykonywania.

- [Dodawanie i usuwanie stron właściwości](../extensibility/adding-and-removing-property-pages.md) opisano sposób dostosowywania stron właściwości dla Twojego własnego projektu.

- [Dodawanie atrybutu do elementu projektu](../extensibility/adding-an-attribute-to-a-project-item.md) został objaśniony sposób dodawania atrybutu do elementu niestandardowego projektu.

- [Utrwalanie właściwości elementu projektu](../extensibility/persisting-the-property-of-a-project-item.md) wyjaśnia, jak utrwalanie właściwości elementu niestandardowego projektu.

- [Zarządzaj projektami usługi universal Windows](../extensibility/managing-universal-windows-projects.md) wyjaśnia, jak zarządzać uniwersalne projekty.