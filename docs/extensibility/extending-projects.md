---
title: Rozszerzanie projektów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14108a304cc5f85c9a870bc66804df7daa98f3ca
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711750"
---
# <a name="extend-projects"></a>Rozszerzanie projektów
Projekty i rozwiązania to sposób, w jaki program Visual Studio organizuje pliki kodu i zasobów w jednostkach kompilacji i wdrażania. Więcej informacji na temat projektów można znaleźć w [programie Projects (Visual Studio SDK).](../extensibility/extending-projects.md)

 Można tworzyć własne typy projektów za pomocą zestawu SDK programu Visual Studio i zestawu pakietów zarządzanych dla projektów, które można pobrać w [ramach pakietu zarządzanego dla projektów.](https://github.com/tunnelvisionlabs/MPFProj10) Aby zrozumieć, w jaki sposób projekty niestandardowe są realizowane, zobacz [Nowa generacja projektu: Pod maską, część pierwsza](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) i Nowa [generacja projektu: Pod maską, część druga](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 W tematach w tej sekcji opisano sposób tworzenia projektów niestandardowych i jak zarządzać różnymi typami rozwiązania programu Visual Studio.

## <a name="in-this-section"></a>W tej sekcji
- [Tworzenie podstawowego systemu projektów, część 1](../extensibility/creating-a-basic-project-system-part-1.md) W tym artykule opisano sposób tworzenia niestandardowego systemu projektu.

- [Tworzenie podstawowego systemu projektów, część 2](../extensibility/creating-a-basic-project-system-part-2.md) W tym artykule opisano sposób tworzenia niestandardowego systemu projektu.

- [Zapisywanie danych w plikach projektu](../extensibility/saving-data-in-project-files.md) W tym artykule wyjaśniono, jak dodać do projektu (<em>.</em> proj*).

- [Weryfikowanie podtypów projektu w czasie wykonywania](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) W tym artykule wyjaśniono, jak zweryfikować podtyp projektu w czasie wykonywania.

- [Dodawanie i usuwanie stron właściwości](../extensibility/adding-and-removing-property-pages.md) W tym artykule wyjaśniono, jak dostosować strony właściwości dla projektu niestandardowego.

- [Dodawanie atrybutu do elementu projektu](../extensibility/adding-an-attribute-to-a-project-item.md) W tym artykule wyjaśniono, jak dodać atrybut do elementu projektu niestandardowego.

- [Utrwalanie właściwości elementu projektu](../extensibility/persisting-the-property-of-a-project-item.md) Wyjaśniono, jak utrwalić właściwości elementu projektu niestandardowego.

- [Zarządzanie uniwersalnymi projektami systemu Windows](../extensibility/managing-universal-windows-projects.md) Wyjaśniono, jak zarządzać projektami uniwersalnymi.
