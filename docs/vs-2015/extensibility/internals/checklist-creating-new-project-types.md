---
title: 'Lista kontrolna: Tworzenie nowych typów projektów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90b48f5969a422ab9d211bb56900cf1b3b41a78b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737356"
---
# <a name="checklist-creating-new-project-types"></a>Lista kontrolna: tworzenie nowych typów projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Należy wykonać kilka zadań, aby utworzyć nowy typ projektu. Poniższa lista kontrolna zawiera przewodnik z tymi zadaniami.  
  
1.  Zaprojektuj funkcjonalność nowego typu projektu. Aby uzyskać więcej informacji, zobacz [decyzje projektowe dotyczące typów projektu](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Ustal, edytory, które są używane dla kodu i innych elementów projektu. Możesz użyć podstawowych lub standardowych edytorów lub można tworzyć i używać edytorów specyficznych dla projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych edytorów i projektantów](../../extensibility/creating-custom-editors-and-designers.md) i [porady: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Ustal poziom współdziałania ze strony elementów projektu będą mieli w **Widok klas** i **przeglądarki obiektów**. Aby uzyskać więcej informacji, zobacz [narzędzi do przeglądania symboli obsługi](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Wyprowadzać nowe klasy, w oparciu o decyzji projektowych, które sporządziłeś wcześniej dla projektów i elementów projektu.  
  
5.  Pisanie kodu dla następujących składników typu projektu:  
  
    -   Fabryka projektu do zarządzania, tworzenie nowych projektów i otworzenie istniejącego projektu. Aby uzyskać więcej informacji, zobacz [tworzenia projektu wystąpień, przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Projekt hierarchii oraz obsługi polecenia. Aby uzyskać więcej informacji, zobacz [nie w kompilacji: Używanie klas HierUtil7 projektu do zaimplementowania typu projektu (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346), [elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md), [podstawowe składnikimodeluprojektu](../../extensibility/internals/project-model-core-components.md)i [MenuCommands programu Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
    -   Zarządzanie elementów projektu, w tym dodawanie projektu do **nowy projekt** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Dodawanie projektu i szablonów elementów projektów](../../extensibility/internals/adding-project-and-project-item-templates.md) i [szablonów elementów i projektów rejestrowanie](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Stan trwały stan projektu i pojedynczych elementów. Aby uzyskać więcej informacji, zobacz [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md). Aby trwałości informacje o rozwiązaniu, zobacz [rozwiązania](../../extensibility/internals/solutions.md).  
  
    -   Niezależnie od właściwości konfiguracji do wyświetlenia w oknie dialogowym właściwości. Aby uzyskać więcej informacji, zobacz [rozszerzanie właściwości](../../extensibility/internals/extending-properties.md).  
  
    -   Właściwości konfiguracji projektu, zaimplementowanego na stronach właściwości, aby wyświetlić właściwości zależne od konfiguracji. Aby uzyskać więcej informacji, zobacz [zarządzanie opcje konfiguracji](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Wyliczanie danych wyjściowych dla wdrożenia. Aby uzyskać więcej informacji, zobacz [konfiguracji projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Projekt uruchamiania usługi. Aby uzyskać więcej informacji, zobacz [elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md) i [podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md).  
  
    -   Obiekty i klasy pochodne `IDispatch`, która jest dostępna w przypadku usługi Automation.  
  
    -   Pliki tabeli poleceń XML (vsct). Aby uzyskać więcej informacji, zobacz [tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Testowanie, debugowanie i Rozpocznij typu projektu.  
  
7.  Wyświetla projekt w **projektu** karcie **Dodaj odwołanie** okno dialogowe, ustawiając `VARIANT_TRUE` jako wartość `VSHPROPID_ShowProjInSolutionPage`. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Utwórz plik Microsoft Installer (.msi), instalowania usługi pakietów VSPackage. Aby uzyskać więcej informacji, zobacz [instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [rejestrowanie typu projektu](../../extensibility/internals/registering-a-project-type.md), i [pakietów VSPackage](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Kiedy należy tworzyć typy projektów](../../extensibility/internals/when-to-create-project-types.md)   
 [Tworzenie typów projektów](../../extensibility/internals/creating-project-types.md)

