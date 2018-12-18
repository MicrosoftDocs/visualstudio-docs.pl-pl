---
title: Elementy modelu projektu | Dokumentacja firmy Microsoft
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
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 818e58af478b3c86c4d0ce9daa9c439681de999e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810373"
---
# <a name="elements-of-a-project-model"></a>Elementy modelu projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Interfejsy i implementacje wszystkich projektów w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] udostępnianie podstawowa struktura: model projektu dla danego typu projektu. Model projektu, czyli pakietu VSPackage, tworzysz służy do tworzenia obiektów, które są zgodne z decyzji projektowych i współdziałały globalne funkcje udostępniane przez środowisko IDE. Chociaż możesz kontrolować, jak element projektu jest trwały, na przykład, możesz nie mają kontroli nad powiadomienia, plik musi zostać utrwalone. Gdy użytkownik Przełącza fokus na elemencie Otwórz projekt, a **Zapisz** na **pliku** menu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] menu pasku kod typu projektu musi przechwytywać polecenie z poziomu środowiska IDE, utrwalanie plików, i Wyślij powiadomienie do środowiska IDE nie jest już zmiany pliku.  
  
 Usługi pakietu VSPackage współdziała z IDE za pośrednictwem usług, które zapewniają dostęp do interfejsów IDE. Na przykład za pośrednictwem usług konkretnego monitora i trasy poleceń i podaj informacje o kontekście dla wybranych ustawień w projekcie. Wszystkie globalne IDE funkcje potrzebne do Twojego pakietu VSPackage są udostępniane przez usługi. Aby uzyskać więcej informacji na temat usług, zobacz [porady: pobieranie usługi](../../extensibility/how-to-get-a-service.md).  
  
 Inne uwagi dotyczące implementacji:  
  
- Modelu tego pojedynczego projektu może zawierać więcej niż jeden typ projektu.  
  
- Typy projektów i fabryk projektów towarzyszącej zostały zarejestrowane niezależnie przy użyciu identyfikatorów GUID.  
  
- Każdy projekt musi mieć w pliku szablonu lub kreatora w celu inicjowania nowego pliku projektu, gdy użytkownik tworzy nowy projekt za pomocą [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfejsu użytkownika. Na przykład [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] szablony zainicjować co przestać .VCPROJ — pliki.  
  
  Na poniższej ilustracji przedstawiono głównych interfejsów, usług i obiektów, które tworzą implementację typowym projekcie. Pomocnika aplikacji HierUtil7, można użyć do tworzenia obiektów i innych standardowy programowania. Aby uzyskać więcej informacji na temat pomocnika aplikacji HierUtil7 zobacz [nie w kompilacji: Używanie klas HierUtil7 projektu do zaimplementowania typu projektu (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
  ![Grafika przedstawiająca usługi Visual Studio modelu projektu](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
  model projektu  
  
  Aby uzyskać więcej informacji dotyczących interfejsów i usług wymienionych na poprzednim rysunku, a inne opcjonalne interfejsy, które nie są uwzględnione w diagramie, zobacz [podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md).  
  
  Projekty mogą obsługiwać poleceń i w związku z tym należy zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs do wzięcia udziału w routingu poleceń za pomocą polecenia kontekstu identyfikatorów GUID.  
  
## <a name="see-also"></a>Zobacz też  
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Nie w kompilacji: Używanie klas projektu HierUtil7 do zaimplementowania typu projektu (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md)   
 [Tworzenie wystąpień projektów przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Porady: uzyskiwanie usługi](../../extensibility/how-to-get-a-service.md)   
 [Tworzenie typów projektów](../../extensibility/internals/creating-project-types.md)

