---
title: 'Lista kontrolna: Tworzenie nowych typów projektów | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5963083239571af43012e1a79576ee80846d80bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709752"
---
# <a name="checklist-create-new-project-types"></a>Lista kontrolna: tworzenie nowych typów projektów
Aby utworzyć nowy typ projektu, należy wykonać kilka zadań. Poniższa lista kontrolna zawiera przewodnik po tych zadaniach:

1. Zaprojektuj funkcjonalność dla nowego typu projektu. Aby uzyskać więcej informacji, zobacz [Decyzje dotyczące projektowania typu projektu](../../extensibility/internals/project-type-design-decisions.md).

2. Określ, które edytory są używane dla kodu i innych elementów projektu. Można użyć podstawowych lub standardowych edytorów lub można tworzyć i używać edytorów specyficznych dla projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych edytorów i projektantów](../../extensibility/creating-custom-editors-and-designers.md) oraz [Jak: Otwórz edytory specyficzne dla projektu](../../extensibility/how-to-open-project-specific-editors.md).

3. Określ poziom uczestnictwa, jaki będą miały elementy projektu w **widoku klasy** i **przeglądarce obiektów**. Aby uzyskać więcej informacji, zobacz [Narzędzia do przeglądania symboli .](../../extensibility/internals/supporting-symbol-browsing-tools.md)

4. Wywodź nowe klasy na podstawie decyzji projektowych, które zostały wcześniej podjęte dla elementów projektu i projektu.

5. Napisz kod dla następujących składników typu projektu:

    - Fabryka projektów, do zarządzania tworzeniem nowych projektów i otwieraniem istniejących projektów. Aby uzyskać więcej informacji, zobacz [Tworzenie wystąpień projektu przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

    - Hierarchia projektu i obsługa poleceń. Aby uzyskać więcej informacji, zobacz [Używanie klas projektu HierUtil7 do zaimplementowania typu projektu (C++),](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346) [elementów modelu projektu,](../../extensibility/internals/elements-of-a-project-model.md) [podstawowych składników modelu projektu](../../extensibility/internals/project-model-core-components.md)i [MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

    - Zarządzanie elementami projektu, w tym dodawanie projektu do okna dialogowego **Nowy projekt.** Aby uzyskać więcej informacji, zobacz [Dodawanie szablonów elementów projektu i projektu](../../extensibility/internals/adding-project-and-project-item-templates.md) oraz [Rejestrowanie szablonów projektów i towarów](../../extensibility/internals/registering-project-and-item-templates.md).

    - Trwałość stanu projektu i poszczególnych elementów. Aby uzyskać więcej informacji, zobacz [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md). Aby uzyskać trwałość informacji o roztworze, zobacz [Rozwiązania](../../extensibility/internals/solutions-overview.md).

    - Właściwości niezależne od konfiguracji do wyświetlenia w oknie Właściwości. Aby uzyskać więcej informacji, zobacz [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md).

    - Właściwości konfiguracji projektu zaimplementowane na stronach właściwości, aby wyświetlić właściwości zależne od konfiguracji. Aby uzyskać więcej informacji, zobacz [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md).

    - Wyliczanie danych wyjściowych do wdrożenia. Aby uzyskać więcej informacji, zobacz [Konfiguracja projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md).

    - Usługi uruchamiania projektu. Aby uzyskać więcej informacji, zobacz [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md) i podstawowe składniki modelu [projektu](../../extensibility/internals/project-model-core-components.md).

    - Obiekty lub klasy pochodzące z `IDispatch`, dostępne dla automatyzacji.

    - tabela poleceń XML (*.vsct*). Aby uzyskać więcej informacji, zobacz [Pliki tabeli poleceń programu Visual Studio (vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

6. Przetestuj, debuguj i uruchom typ projektu.

7. Wyświetlanie projektu na karcie **Projekt** w oknie dialogowym Dodawanie `VSHPROPID_ShowProjInSolutionPage` **odwołania** przez ustawienie `VARIANT_TRUE` jako wartości dla programu . Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.

8. Utwórz plik Instalatora Microsoft *(msi)* do zainstalowania pakietu VSPackages. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietów VSPackages w Instalatorze Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [Rejestrowanie typu projektu](../../extensibility/internals/registering-a-project-type.md)i [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="see-also"></a>Zobacz też
- [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Kiedy tworzyć typy projektów](../../extensibility/internals/when-to-create-project-types.md)
- [Tworzenie typów projektów](../../extensibility/internals/creating-project-types.md)
