---
title: Elementy modelu projektu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e14086ea395ffe65a52f47d0bfaa320fb19bc8f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623102"
---
# <a name="elements-of-a-project-model"></a>Elementy modelu projektu
Interfejsy i implementacje wszystkich projektów w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] udostępnianie podstawowa struktura: model projektu dla danego typu projektu. Model projektu, czyli pakietu VSPackage, tworzysz służy do tworzenia obiektów, które są zgodne z decyzji projektowych i współdziałały globalne funkcje udostępniane przez środowisko IDE. Chociaż możesz kontrolować, jak element projektu jest trwały, na przykład, możesz nie mają kontroli nad powiadomienia, plik musi zostać utrwalone. Gdy użytkownik Przełącza fokus na elemencie Otwórz projekt, a **Zapisz** na **pliku** menu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menu pasku kod typu projektu musi przechwytywać polecenie z poziomu środowiska IDE, utrwalanie plików, i Wyślij powiadomienie do środowiska IDE nie jest już zmiany pliku.

 Usługi pakietu VSPackage współdziała z IDE za pośrednictwem usług, które zapewniają dostęp do interfejsów IDE. Na przykład za pośrednictwem usług konkretnego monitora i trasy poleceń i podaj informacje o kontekście dla wybranych ustawień w projekcie. Wszystkie globalne IDE funkcje potrzebne do Twojego pakietu VSPackage są udostępniane przez usługi. Aby uzyskać więcej informacji na temat usług, zobacz [jak: Usługi](../../extensibility/how-to-get-a-service.md).

 Inne uwagi dotyczące implementacji:

- Modelu tego pojedynczego projektu może zawierać więcej niż jeden typ projektu.

- Typy projektów i fabryk projektów towarzyszącej zostały zarejestrowane niezależnie przy użyciu identyfikatorów GUID.

- Każdy projekt musi mieć w pliku szablonu lub kreatora w celu inicjowania nowego pliku projektu, gdy użytkownik tworzy nowy projekt za pomocą [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika. Na przykład [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] szablony zainicjować co przestać .VCPROJ — pliki.

  Na poniższej ilustracji przedstawiono głównych interfejsów, usług i obiektów, które tworzą implementację typowym projekcie. Można użyć pomocnika aplikacji `HierUtil7`, aby utworzyć obiekty źródłowe i innych standardowy programowania. Aby uzyskać więcej informacji na temat `HierUtil7` pomocnika aplikacji, zobacz [HierUtil7 Użyj projektu klasy do zaimplementowania typu projektu (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

  ![Grafiki modelu projektu programu Visual Studio](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") modelu projektu

  Aby uzyskać więcej informacji dotyczących interfejsów i usług wymienionych na poprzednim rysunku, a inne opcjonalne interfejsy, które nie są uwzględnione w diagramie, zobacz [podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md).

  Projekty mogą obsługiwać poleceń i w związku z tym należy zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs do wzięcia udziału w routingu poleceń za pomocą polecenia kontekstu identyfikatorów GUID.

## <a name="see-also"></a>Zobacz także
- [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Użycie klasy projektu HierUtil7 w celu zaimplementowania typu projektu (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md)
- [Tworzenie wystąpień projektów przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Instrukcje: Uzyskiwanie usługi](../../extensibility/how-to-get-a-service.md)
- [Tworzenie typów projektów](../../extensibility/internals/creating-project-types.md)
