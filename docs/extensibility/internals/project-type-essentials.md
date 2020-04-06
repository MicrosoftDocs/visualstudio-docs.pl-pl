---
title: Podstawowe informacje o typie projektu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b44da532207668d9526aec0ccdcab027b94184e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706386"
---
# <a name="project-type-essentials"></a>Podstawowe informacje o typach projektów
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zawiera kilka typów projektów dla [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]języków, takich jak lub . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]umożliwia również tworzenie własnych typów projektów.

 Jeśli chcesz tylko dodać niestandardowe polecenia, edytory [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]lub okna narzędzi do programu , możesz to zrobić bez tworzenia nowego typu projektu. Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Rozszerzenia edytora i usługi językowej](../../extensibility/editor-and-language-service-extensions.md)

- [Rozszerzanie i dostosowywanie okien narzędzi](../../extensibility/extending-and-customizing-tool-windows.md)

  Podobnie, jeśli chcesz dostosować zachowanie dostarczonych [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] typów projektów, można to zrobić za pomocą podtypów projektu. Aby uzyskać więcej informacji, zobacz [Podtypy projektu](../../extensibility/internals/project-subtypes.md).

  Należy utworzyć nowy typ projektu dla projektów, które [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] są [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] oparte na języku innym niż i jeśli chcesz obsługiwać co najmniej jeden z następujących elementów:

- Kompilacja

- Wdrożenie

- Wiele konfiguracji

- Kontrola źródła

- Debugowanie

- Elementy projektu w Eksploratorze rozwiązań

- Okna dialogowe **Otwieranie projektu** lub **nowy projekt**

- Zagnieżdżanie projektów

- Aby uzyskać więcej informacji na temat możliwości typów projektów, zobacz następujące informacje:

- Typy projektów są obiekty w VSPackage, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] które implementują zestaw interfejsów oczekuje. Jeśli używasz języka C# do opracowania typu projektu, klasy projektu managed package framework implementują niezbędne interfejsy dla Ciebie i umożliwiają dziedziczenie tej implementacji. Aby uzyskać więcej informacji, zobacz [Zaimplementowanie typu projektu (C#) za pomocą struktury pakietu zarządzanego.](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)

- Dla deweloperów języka C++ klasy w bibliotece HierUtil działają w podobny sposób. Aby uzyskać więcej informacji, zobacz [Nie w kompilacji: Używanie klas projektu HierUtil7 do zaimplementowania typu projektu (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

- Typy projektów mogą obsługiwać dane inne niż typowe pliki kodu źródłowego, które są wbudowane w zestaw .exe lub dll. Na przykład [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekty baz danych zawierają odwołania do plików skryptów i zapytań przechowywanych na dysku i dodają polecenia do **Eksploratora rozwiązań** w celu wykonania skryptów i zapytań względem bazy danych, ale projekty nie obsługują zachowania kompilacji. Aby uzyskać więcej informacji, zobacz [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).

- Typ projektu nie musi w ogóle używać plików. Na przykład typ projektu może przechowywać wszystkie swoje dane w bazie danych. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]daje typom projektów pełną kontrolę nad tym, jak utrwalają dane dla projektów i elementów projektu. Aby uzyskać więcej informacji, zobacz [Decyzje dotyczące projektu](../../extensibility/internals/project-type-design-decisions.md).

- Typy projektów muszą zawierać *fabrykę projektu*, która jest obiektem, który tworzy wystąpienie typu projektu za każdym razem, gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zostanie powiedziane o otwarciu lub utworzeniu projektu opartego na tym typie projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie wystąpień projektu przy użyciu fabryk projektu](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Typy projektów muszą dostarczać szablony dla projektów i elementów projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]używa szablonów, gdy użytkownicy tworzą nowe projekty i dodają nowe elementy do istniejących projektów. Aby uzyskać więcej informacji, zobacz [Dodawanie szablonów elementów projektu i projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Typy projektów mogą obsługiwać wiele konfiguracji, takich jak debugowanie i zwalnianie. Użytkownicy mogą zmieniać różne konfiguracje projektu przy użyciu stron właściwości, które można podać. Aby uzyskać więcej informacji, zobacz [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>Zobacz też
- [Wdrażanie typów projektów](../../extensibility/internals/deploying-project-types.md)
