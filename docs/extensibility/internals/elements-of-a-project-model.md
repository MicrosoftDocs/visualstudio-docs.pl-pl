---
title: Elementy modelu projektu | Microsoft Docs
description: Dowiedz się więcej o elementach modelu projektu oraz o sposobie, w jaki interfejsy i implementacje wszystkich projektów w programie Visual Studio udostępniają podstawową strukturę.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e366b2923d5903f00241db0a6b71017dc25f3dee
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480047"
---
# <a name="elements-of-a-project-model"></a>Elementy modelu projektu
Interfejsy i implementacje wszystkich projektów w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] udostępniają podstawową strukturę: model projektu dla typu projektu. W modelu projektu, który jest pakietu VSPackage, tworzysz obiekty, które są zgodne z decyzjami projektowymi i pracują z funkcjami globalnymi dostępnymi przez IDE. Chociaż kontrolujesz sposób utrwalania elementu projektu, na przykład nie kontrolujesz powiadomienia, że plik musi być utrwalony. Gdy użytkownik umieści fokus w otwartym elemencie projektu i wybierze pozycję **Zapisz** w menu **plik** na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pasku menu, kod typu projektu musi przechwycić polecenie z IDE, zachować plik i wysłać powiadomienie z powrotem do IDE, że plik nie jest już zmieniany.

 Pakietu VSPackage współdziała z środowiskiem IDE za pomocą usług zapewniających dostęp do interfejsów IDE. Na przykład za pomocą określonych usług można monitorować i kierować polecenia oraz udostępniać informacje kontekstowe dotyczące wybranych elementów projektu. Wszystkie funkcje globalne IDE pakietu VSPackage są udostępniane przez usługi. Aby uzyskać więcej informacji na temat usług, zobacz [How to: get a Service](../../extensibility/how-to-get-a-service.md).

 Inne zagadnienia dotyczące implementacji:

- Jeden model projektu może zawierać więcej niż jeden typ projektu.

- Typy projektów i fabryki projektów programu Attendant są rejestrowane niezależnie od identyfikatorów GUID.

- Każdy projekt musi mieć plik lub Kreator szablonu, aby zainicjować nowy plik projektu, gdy użytkownik tworzy nowy projekt za pomocą [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika. Na przykład [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Szablony inicjują, co ostatecznie staną się plikami VCPROJ.

  Na poniższej ilustracji przedstawiono podstawowe interfejsy, usługi i obiekty tworzące typową implementację projektu. Możesz użyć pomocnika aplikacji, `HierUtil7` Aby utworzyć obiekty bazowe i inne typowe programowanie. Aby uzyskać więcej informacji na temat `HierUtil7` pomocnika aplikacji, zobacz [Korzystanie z klas projektów HierUtil7 do implementowania typu projektu (C++)](/previous-versions/bb166212(v=vs.100)).

  ![Grafika modelu projektu programu Visual Studio](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") Model projektu

  Aby uzyskać więcej informacji na temat interfejsów i usług wymienionych na poprzednim diagramie oraz innych opcjonalnych interfejsów, które nie znajdują się na diagramie, zobacz [podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md).

  Projekty mogą obsługiwać polecenia i w związku z tym muszą implementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs, aby uczestniczyć w kierowaniu poleceń przez identyfikatory GUID kontekstu poleceń.

## <a name="see-also"></a>Zobacz też
- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Korzystanie z klas projektów HierUtil7 do implementowania typu projektu (C++)](/previous-versions/bb166212(v=vs.100))
- [Podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md)
- [Tworzenie wystąpień projektu przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Instrukcje: Uzyskiwanie usługi](../../extensibility/how-to-get-a-service.md)
- [Tworzenie typów projektów](../../extensibility/internals/creating-project-types.md)