---
title: Elementy modelu projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f3b07068939e34b5c9e9487761177c0e12f5654
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700115"
---
# <a name="elements-of-a-project-model"></a>Elementy modelu projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Interfejsy i implementacje wszystkich projektów w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] udostępniają podstawową strukturę: model projektu dla typu projektu. W modelu projektu, który jest pakietu VSPackage, tworzysz obiekty, które są zgodne z decyzjami projektowymi i pracują z funkcjami globalnymi dostępnymi przez IDE. Chociaż kontrolujesz sposób utrwalania elementu projektu, na przykład nie kontrolujesz powiadomienia, że plik musi być utrwalony. Gdy użytkownik umieści fokus w otwartym elemencie projektu i wybierze pozycję **Zapisz** w menu **plik** na [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pasku menu, kod typu projektu musi przechwycić polecenie z IDE, zachować plik i wysłać powiadomienie z powrotem do IDE, że plik nie jest już zmieniany.  
  
 Pakietu VSPackage współdziała z środowiskiem IDE za pomocą usług zapewniających dostęp do interfejsów IDE. Na przykład za pomocą określonych usług można monitorować i kierować polecenia oraz udostępniać informacje kontekstowe dotyczące wybranych elementów projektu. Wszystkie funkcje globalne IDE pakietu VSPackage są udostępniane przez usługi. Aby uzyskać więcej informacji na temat usług, zobacz [How to: get a Service](../../extensibility/how-to-get-a-service.md).  
  
 Inne zagadnienia dotyczące implementacji:  
  
- Jeden model projektu może zawierać więcej niż jeden typ projektu.  
  
- Typy projektów i fabryki projektów programu Attendant są rejestrowane niezależnie od identyfikatorów GUID.  
  
- Każdy projekt musi mieć plik lub Kreator szablonu, aby zainicjować nowy plik projektu, gdy użytkownik tworzy nowy projekt za pomocą [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfejsu użytkownika. Na przykład [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] Szablony inicjują, co ostatecznie staną się plikami VCPROJ.  
  
  Na poniższej ilustracji przedstawiono podstawowe interfejsy, usługi i obiekty tworzące typową implementację projektu. Można użyć pomocnika aplikacji, HierUtil7, do tworzenia obiektów podstawowych i innych wzorców programistycznych. Aby uzyskać więcej informacji na temat pomocnika aplikacji HierUtil7, zobacz [nie w kompilacji: przy użyciu klas projektu HierUtil7 w celu zaimplementowania typu projektu (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
  ![Grafika modelu projektu programu Visual Studio](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
  model projektu  
  
  Aby uzyskać więcej informacji na temat interfejsów i usług wymienionych na poprzednim diagramie oraz innych opcjonalnych interfejsów, które nie znajdują się na diagramie, zobacz [podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md).  
  
  Projekty mogą obsługiwać polecenia i w związku z tym muszą implementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs, aby uczestniczyć w kierowaniu poleceń przez identyfikatory GUID kontekstu poleceń.  
  
## <a name="see-also"></a>Zobacz też  
 [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Nie w kompilacji: używanie klas projektu HierUtil7 do implementowania typu projektu (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md)   
 [Tworzenie wystąpień projektu przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Instrukcje: Uzyskiwanie usługi](../../extensibility/how-to-get-a-service.md)   
 [Tworzenie typów projektów](../../extensibility/internals/creating-project-types.md)
