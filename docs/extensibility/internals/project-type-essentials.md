---
title: Podstawowe informacje o typie projektu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 435d3ca0e35911754cac1e37abb276939109a0b3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725407"
---
# <a name="project-type-essentials"></a>Podstawowe informacje o typach projektów
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zawiera kilka typów projektów dla języków, takich jak [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] lub [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] również umożliwia tworzenie własnych typów projektów.

 Jeśli chcesz tylko dodać niestandardowe polecenia, edytory lub okna narzędzi do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], możesz to zrobić bez tworzenia nowego typu projektu. Więcej informacji znajduje się w następujących tematach:

- [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Rozszerzenia edytora i usługi językowej](../../extensibility/editor-and-language-service-extensions.md)

- [Rozszerzanie i dostosowywanie okien narzędzi](../../extensibility/extending-and-customizing-tool-windows.md)

  Podobnie, jeśli chcesz dostosować zachowanie podanych [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] typy projektów, możesz to zrobić przy użyciu podtypów projektu. Aby uzyskać więcej informacji, zobacz [podtypy projektów](../../extensibility/internals/project-subtypes.md).

  Należy utworzyć nowy typ projektu dla projektów opartych na języku innym niż [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], jeśli chcesz obsługiwać co najmniej jedną z następujących czynności:

- Kompilacja

- wdrażania

- Wiele konfiguracji

- Kontrola źródła

- Debugowanie

- Elementy projektu w Eksplorator rozwiązań

- Okna dialogowe **Otwórz projekt** lub **Nowy projekt**

- Zagnieżdżanie projektu

- Aby uzyskać więcej informacji na temat możliwości typów projektów, zobacz następujące tematy:

- Typy projektów to obiekty w pakietu VSPackage, które implementują zestaw interfejsów [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oczekiwać. Jeśli używasz C# programu do tworzenia typu projektu, klasy projektu struktury pakietów zarządzanych implementują niezbędne interfejsy i umożliwiają dziedziczenie tej implementacji. Aby uzyskać więcej informacji, zobacz [Używanie struktury pakietu zarządzanego do implementowania typu projektu (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).

- W C++ przypadku deweloperów klasy w bibliotece HierUtil działają w podobny sposób. Aby uzyskać więcej informacji, zobacz [nie w kompilacji: używanie klas projektu HierUtil7 do implementowania typu projektuC++()](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

- Typy projektów mogą obsługiwać dane inne niż typowe pliki kodu źródłowego, które kompilują do zestawu. exe lub. dll. Na przykład [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekty bazy danych zawierają odwołania do plików skryptów i zapytań przechowywanych na dysku, a następnie Dodaj polecenia do **Eksplorator rozwiązań** , aby wykonać skrypty i zapytania względem bazy danych, ale projekty nie obsługują zachowania kompilacji. Aby uzyskać więcej informacji, zobacz [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).

- Typ projektu nie musi używać plików w ogóle. Na przykład typ projektu może przechowywać wszystkie jego dane w bazie danych. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zapewnia, że typy projektów mają pełną kontrolę nad sposobem utrwalania danych dla projektów i elementów projektu. Aby uzyskać więcej informacji, zobacz [decyzje projektowe typu projektu](../../extensibility/internals/project-type-design-decisions.md).

- Typy projektów muszą dostarczać *fabrykę projektu*, która jest obiektem, który tworzy wystąpienie typu projektu za każdym razem, gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest wyświetlany, aby otworzyć lub utworzyć projekt oparty na tym typie projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie wystąpień projektu przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Typy projektów muszą dostarczać szablony dla projektów i elementów projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] używa szablonów, gdy użytkownicy tworzą nowe projekty i dodają nowe elementy do istniejących projektów. Aby uzyskać więcej informacji, zobacz [Dodawanie projektów i szablonów elementów projektów](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Typy projektów mogą obsługiwać wiele konfiguracji, takich jak debugowanie i wydanie. Użytkownicy mogą zmieniać różne konfiguracje projektu przy użyciu stron właściwości, które dostarczasz. Aby uzyskać więcej informacji, zobacz [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>Zobacz także
- [Wdrażanie typów projektów](../../extensibility/internals/deploying-project-types.md)