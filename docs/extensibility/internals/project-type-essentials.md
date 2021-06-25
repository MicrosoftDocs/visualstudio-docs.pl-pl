---
title: Typ projektu Essentials | Microsoft Docs
description: Dowiedz się, kiedy należy utworzyć typ projektu i kiedy można rozszerzyć istniejący typ projektu przy użyciu podtypów projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 051e7b76edd4559914307459fdcbdf1b7c0b600e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903561"
---
# <a name="project-type-essentials"></a>Podstawowe informacje o typach projektów
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Program zawiera kilka typów projektów dla języków takich [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] jak lub [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umożliwia również tworzenie własnych typów projektów.

 Jeśli chcesz tylko dodać niestandardowe polecenia, edytory lub okna narzędzi do programu , możesz to zrobić bez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tworzenia nowego typu projektu. Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Rozszerzenia edytora i usługi językowej](../../extensibility/editor-and-language-service-extensions.md)

- [Rozszerzanie i dostosowywanie okien narzędzi](../../extensibility/extending-and-customizing-tool-windows.md)

  Podobnie, jeśli chcesz dostosować zachowanie typów dostarczanych i projektów, możesz to zrobić przy [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] użyciu podtypów projektu. Aby uzyskać więcej informacji, zobacz [Podtypy projektów](../../extensibility/internals/project-subtypes.md).

  Należy utworzyć nowy typ projektu dla projektów, które są oparte na języku innym niż i jeśli chcesz obsługiwać co najmniej [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] jeden z następujących:

- Kompilacja

- Wdrożenie

- Wiele konfiguracji

- Kontrola źródła

- Debugowanie

- Elementy projektu w Eksplorator rozwiązań

- Okna **dialogowe Otwieranie** projektu **lub** Nowy projekt

- Zagnieżdżanie projektu

- Aby uzyskać więcej informacji na temat możliwości typów projektów, zobacz następujące informacje:

- Typy projektów są obiektami w pakietach VSPackage, które implementują zestaw interfejsów, których [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oczekuje. Jeśli używasz języka C# do opracowywania typu projektu, klasy projektów Managed Package Framework implementują niezbędne interfejsy i umożliwiają dziedziczenie tej implementacji. Aby uzyskać więcej informacji, zobacz Implementowanie typu projektu [(C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)przy użyciu struktury pakietów zarządzanych.

- W przypadku deweloperów języka C++ klasy w bibliotece HierUtil działają w podobny sposób. Aby uzyskać więcej informacji, zobacz [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type (C++) (Nie](/previous-versions/bb166212(v=vs.100))w kompilacji: używanie klas projektów HierUtil7 do implementowanie typu projektu (C++).

- Typy projektów mogą obsługiwać dane inne niż typowe pliki kodu źródłowego, które są .exe lub .dll zestawu. Na przykład projekty bazy danych zawierają odwołania do plików skryptów i zapytań przechowywanych na dysku oraz dodają polecenia do programu Eksplorator rozwiązań służące do wykonywania skryptów i zapytań względem bazy danych, ale projekty nie obsługują zachowania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kompilacji.  Aby uzyskać więcej informacji, zobacz [Otwieranie i zapisywanie elementów projektu.](../../extensibility/internals/opening-and-saving-project-items.md)

- Typ projektu nie musi w ogóle używać plików. Na przykład typ projektu może przechowywać wszystkie swoje dane w bazie danych. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zapewnia typom projektów pełną kontrolę nad tym, jak utrwalają dane projektów i elementów projektu. Aby uzyskać więcej informacji, zobacz [Project Type Design Decisions (Decyzje projektowe dotyczące typu projektu).](../../extensibility/internals/project-type-design-decisions.md)

- Typy projektów muszą zapewniać fabrykę projektów *,* która jest obiektem, który tworzy wystąpienie typu projektu za każdym razem, gdy zostanie nakadanie do otwarcia lub utworzenia projektu opartego na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tym typie projektu. Aby uzyskać więcej informacji, zobacz [Creating Project Instances By Using Project Factories (Tworzenie wystąpień projektu przy użyciu fabryk projektów).](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

- Typy projektów muszą dostarczać szablony dla projektów i elementów projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] używa szablonów, gdy użytkownicy tworzą nowe projekty i dodają nowe elementy do istniejących projektów. Aby uzyskać więcej informacji, zobacz [Dodawanie szablonów projektów i elementów projektu.](../../extensibility/internals/adding-project-and-project-item-templates.md)

- Typy projektów mogą obsługiwać wiele konfiguracji, takich jak debugowanie i wydanie. Użytkownicy mogą zmieniać różne konfiguracje projektu przy użyciu poszczególnych stron właściwości. Aby uzyskać więcej informacji, zobacz [Zarządzanie opcjami konfiguracji.](../../extensibility/internals/managing-configuration-options.md)

## <a name="see-also"></a>Zobacz też
- [Wdrażanie typów projektów](../../extensibility/internals/deploying-project-types.md)