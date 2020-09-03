---
title: 'Lista kontrolna: tworzenie nowych typów projektów | Microsoft Docs'
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
ms.openlocfilehash: 9372762f713b6a5ec78a92eeb96e8a616101b5bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "84183395"
---
# <a name="checklist-create-new-project-types"></a>Lista kontrolna: tworzenie nowych typów projektów
Aby utworzyć nowy typ projektu, należy wykonać kilka zadań. Poniższa lista kontrolna zawiera Przewodnik po tych zadaniach:

1. Zaprojektuj funkcjonalność dla nowego typu projektu. Aby uzyskać więcej informacji, zobacz [decyzje projektowe typu projektu](../../extensibility/internals/project-type-design-decisions.md).

2. Określ, które edytory są używane do kodu i innych elementów projektu. Można korzystać z edytorów podstawowych lub standardowych lub można tworzyć i używać edytorów specyficznych dla projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych edytorów i projektantów](../../extensibility/creating-custom-editors-and-designers.md) oraz [instrukcje: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md).

3. Określ poziom uczestnictwa elementów projektu w **Widok klasy** i **Przeglądarka obiektów**. Aby uzyskać więcej informacji, zobacz [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md).

4. Utwórz nowe klasy w oparciu o decyzje projektowe, które zostały wcześniej wykonane dla projektu i elementów projektu.

5. Napisz kod dla następujących składników typu projektu:

    - Fabryka projektów do zarządzania tworzeniem nowych projektów i otwierania istniejących projektów. Aby uzyskać więcej informacji, zobacz [Tworzenie wystąpień projektu przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

    - Obsługa poleceń i hierarchii projektu. Aby uzyskać więcej informacji, zobacz [Korzystanie z klas projektów HierUtil7 do implementowania typu projektu (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346), [elementów modelu projektu](../../extensibility/internals/elements-of-a-project-model.md), [składników podstawowych modelu projektu](../../extensibility/internals/project-model-core-components.md)i [MenuCommands a OleMenuCommands](/visualstudio/misc/menucommands-vs-olemenucommands?view=vs-2015).

    - Zarządzanie elementami projektu, w tym dodawanie projektu do okna dialogowego **Nowy projekt** . Aby uzyskać więcej informacji, zobacz [Dodawanie szablonów projektu i elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md) oraz [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md).

    - Trwałość stanu projektu i poszczególnych elementów. Aby uzyskać więcej informacji, zobacz [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md). Aby uzyskać informacje o trwałości informacji o rozwiązaniach, zobacz [rozwiązania](../../extensibility/internals/solutions-overview.md).

    - Właściwości niezależne od konfiguracji, które mają być wyświetlane w okno Właściwości. Aby uzyskać więcej informacji, zobacz [rozszerzając właściwości](../../extensibility/internals/extending-properties.md).

    - Właściwości konfiguracji projektu zgodnie z zaimplementowanymi na stronach właściwości, aby pokazać właściwości zależne od konfiguracji. Aby uzyskać więcej informacji, zobacz [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md).

    - Wyliczanie danych wyjściowych dla wdrożenia. Aby uzyskać więcej informacji, zobacz [Konfiguracja projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md).

    - Usługi uruchomieniowe projektu. Aby uzyskać więcej informacji, zobacz [elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md) i [podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md).

    - Obiekty lub klasy pochodne `IDispatch` , dostępne dla automatyzacji.

    - Pliki tabeli poleceń XML (*. vsct*). Aby uzyskać więcej informacji, zobacz [pliki tabeli poleceń programu Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

6. Przetestuj, Debuguj i uruchamiaj typ projektu.

7. Wyświetl projekt na karcie **projekt** okna dialogowego **Dodaj odwołanie** , ustawiając `VARIANT_TRUE` jako wartość dla `VSHPROPID_ShowProjInSolutionPage` . Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.

8. Utwórz plik Instalatora Microsoft (*MSI*) na potrzeby instalacji pakietów VSPackage. Aby uzyskać więcej informacji, zobacz [Install pakietów VSPackage with Instalator Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [register the Project Type](../../extensibility/internals/registering-a-project-type.md)and [pakietów VSPackage](../../extensibility/internals/vspackages.md).

## <a name="see-also"></a>Zobacz też
- [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Kiedy tworzyć typy projektów](../../extensibility/internals/when-to-create-project-types.md)
- [Tworzenie typów projektów](../../extensibility/internals/creating-project-types.md)
