---
title: Rozszerzanie projektów | Microsoft Docs
description: Dowiedz się, jak tworzyć własne niestandardowe typy projektów w zestawie Visual Studio SDK oraz jak zarządzać różnymi typami rozwiązań programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 997f4e32007af641b24ba933d2c891e447382786
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895833"
---
# <a name="extend-projects"></a>Rozwiń projekty
Projekty i rozwiązania są sposobem, w jaki program Visual Studio organizuje kod i pliki zasobów w ramach kompilacji i jednostek wdrożenia. Więcej informacji na temat projektów można znaleźć w [projektach (Visual Studio SDK)](../extensibility/extending-projects.md).

 Możesz tworzyć własne typy projektów za pomocą zestawu Visual Studio SDK i zarządzanej struktury pakietów dla projektów, które można pobrać w [zarządzanej strukturze pakietów dla projektów](https://github.com/tunnelvisionlabs/MPFProj10). Aby zrozumieć, w jaki sposób są implementowane projekty niestandardowe, zobacz [Nowa generacja projektu: pod okapem, część pierwszej](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) i [generowanie nowego projektu: pod okapem, druga część](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 W tematach w tej sekcji opisano sposób tworzenia projektów niestandardowych i zarządzania różnymi typami rozwiązań programu Visual Studio.

## <a name="in-this-section"></a>W tej sekcji
- [Tworzenie podstawowego systemu projektu, część 1](../extensibility/creating-a-basic-project-system-part-1.md) Opisuje sposób tworzenia niestandardowego systemu projektu.

- [Tworzenie podstawowego systemu projektu, część 2](../extensibility/creating-a-basic-project-system-part-2.md) Opisuje sposób tworzenia niestandardowego systemu projektu.

- [Zapisz dane w plikach projektu](../extensibility/saving-data-in-project-files.md) Wyjaśnia, jak dodać do projektu (<em>.</em> proj *).

- [Weryfikuj podtypy projektu w czasie wykonywania](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) Wyjaśnia, jak zweryfikować podtyp projektu w czasie wykonywania.

- [Dodawanie i usuwanie stron właściwości](../extensibility/adding-and-removing-property-pages.md) Wyjaśnia, jak dostosować strony właściwości dla projektu niestandardowego.

- [Dodawanie atrybutu do elementu projektu](../extensibility/adding-an-attribute-to-a-project-item.md) Wyjaśnia, jak dodać atrybut do niestandardowego elementu projektu.

- [Utrwalanie właściwości elementu projektu](../extensibility/persisting-the-property-of-a-project-item.md) Wyjaśnia, jak utrwalać właściwości niestandardowego elementu projektu.

- [Zarządzanie projektami uniwersalnymi systemu Windows](../extensibility/managing-universal-windows-projects.md) Wyjaśnia, jak zarządzać projektami uniwersalnymi.
