---
title: Zagnieżdżanie projektów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e3a0fae42dc7bf1497e3d0d4a9d23f9cab50675
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "68180417"
---
# <a name="nesting-projects"></a>Zagnieżdżanie projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Deweloperzy aplikacji korporacyjnych korzystających z pakietu programu VS mogą wygodnie grupować podobne typy projektów w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] przy użyciu *zagnieżdżania projektu*. Na przykład projekt szablon przedsiębiorstwa używa zagnieżdżonych projektów do grupowania projektów w kategorii. Projekty fasady biznesowej, projekty interfejsu użytkownika sieci Web i tak dalej są pogrupowane w jednej kategorii.  
  
 W tym scenariuszu nie ma żadnego limitu liczby projektów, które deweloper może zagnieżdżać w każdym projekcie nadrzędnym, Chociaż deweloper może programowo wprowadzić limity. Ten typ grupowania może również spowodować cykliczność, w takim przypadku projekty tego samego typu co projekt podrzędny mogą być zagnieżdżane w elemencie podrzędnym, aby stał się podprojektem elementu podrzędnego, który jest podprojektem elementu nadrzędnego.  
  
 Zagnieżdżanie projektu nie jest wewnętrzną częścią [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Należy napisać kod w celu włączenia zagnieżdżania i zagnieżdżania projektu w ramach projektów podrzędnych. Projekt nadrzędny jest specjalnym pakietu VSPackage lub typem projektu, utworzonym i zarejestrowanym przy użyciu własnego identyfikatora GUID, który zawiera kod, który jest wymagany do wdrożenia zagnieżdżania projektu.  
  
 Przykład zagnieżdżonych projektów można znaleźć w C# przykładowym projekcie zagnieżdżonym.  
  
## <a name="nested-projects-example"></a>Przykład zagnieżdżonych projektów  
 ![Nested Projects Solution](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Przykład zagnieżdżonych projektów  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: implementowanie projektów zagnieżdżonych](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Zagadnienia dotyczące zwalniania i ponownego ładowania zagnieżdżonych projektów](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Obsługa kreatora dla zagnieżdżonych projektów](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Rejestrowanie szablonów projektu i elementów](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementowanie obsługi poleceń dla zagnieżdżonych projektów](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Filtrowanie okna dialogowego AddItem dla zagnieżdżonych projektów](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parametry kontekstu](../../extensibility/internals/context-parameters.md)   
 [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
