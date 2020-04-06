---
title: Elementy modelu projektu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf847e35878dc84bb32fe81053c01c23e565fc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708523"
---
# <a name="elements-of-a-project-model"></a>Elementy modelu projektu
Interfejsy i implementacje wszystkich [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektów w współużytkuje podstawową strukturę: model projektu dla typu projektu. W modelu projektu, który jest VSPackage tworzysz obiekty, które są zgodne z decyzjami projektowymi i współpracować z globalnymi funkcjami dostarczonymi przez IDE. Chociaż można kontrolować, jak element projektu jest zachowywany, na przykład nie kontrolować powiadomienie, że plik musi być utrwalony. Gdy użytkownik umieszcza fokus na otwartym elemencie projektu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i wybiera **Zapisz** w menu **Plik** na pasku menu, kod typu projektu musi przechwycić polecenie z IDE, utrwalić plik i wysłać powiadomienie z powrotem do IDE, że plik nie jest już zmieniony.

 Usługa VSPackage współdziała z IDE za pośrednictwem usług, które zapewniają dostęp do interfejsów IDE. Na przykład za pośrednictwem określonych usług można monitorować i trasy poleceń i podać informacje kontekstowe dla wyborów dokonanych w projekcie. Wszystkie globalne funkcje IDE potrzebne dla vsPackage jest dostarczana przez usługi. Aby uzyskać więcej informacji o usługach, zobacz [Jak: Pobierz usługę](../../extensibility/how-to-get-a-service.md).

 Inne zagadnienia dotyczące wdrażania:

- Pojedynczy model projektu może zawierać więcej niż jeden typ projektu.

- Typy projektów i towarzyszące fabryki projektów są rejestrowane niezależnie za pomocą identyfikatorów GUID.

- Każdy projekt musi mieć plik szablonu lub kreatora, aby zainicjować nowy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plik projektu, gdy użytkownik tworzy nowy projekt za pośrednictwem interfejsu użytkownika. Na przykład [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] szablony inicjują, co ostatecznie stać się .vcproj plików.

  Na poniższej ilustracji przedstawiono interfejsy podstawowe, usługi i obiekty, które tworzą typowe implementacji projektu. Można użyć pomocnika aplikacji, `HierUtil7`aby utworzyć obiekty leżące pod spodem i inne programowanie standardowego. Aby uzyskać więcej `HierUtil7` informacji na temat pomocnika aplikacji, zobacz [Używanie klas projektu HierUtil7 do zaimplementowania typu projektu (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

  ![Grafika przedstawiająca model projektu programu Visual Studio](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") Model projektu

  Aby uzyskać więcej informacji na temat interfejsów i usług wymienionych na poprzednim diagramie i innych opcjonalnych interfejsów nieuwzględnianych na diagramie, zobacz [Podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md).

  Projekty mogą obsługiwać polecenia i <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> dlatego muszą implementować interfejs, aby uczestniczyć w routingu poleceń za pośrednictwem identyfikatorów GUID kontekstu polecenia.

## <a name="see-also"></a>Zobacz też
- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Zaimplementowanie typu projektu (C++) za pomocą klas projektu HierUtil7](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Podstawowe komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md)
- [Tworzenie wystąpień projektu przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Jak: Uzyskaj usługę](../../extensibility/how-to-get-a-service.md)
- [Tworzenie typów projektów](../../extensibility/internals/creating-project-types.md)
