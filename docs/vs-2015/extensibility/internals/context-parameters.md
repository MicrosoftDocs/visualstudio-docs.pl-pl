---
title: Parametry kontekstu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 679bf567d2f44564d31d70b62c8663e665e1ea65
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697283"
---
# <a name="context-parameters"></a>Parametry kontekstu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanym środowisku programistycznym (IDE), możesz dodać kreatorów, aby **nowy projekt**, **Dodaj nowy element**, lub **Dodaj projekt Sub** okien dialogowych. Dodano kreatorów są dostępne na **pliku** menu lub klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**. IDE przekazuje parametry kontekstu wykonania kreatora. Parametry kontekstu Definiowanie stanu projektu, gdy IDE wywołuje kreatora.  
  
 IDE rozpoczyna kreatory, ustawiając <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> flagi w wywołaniu IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metody dla projektu. Po ustawieniu projektu mogą powodować `IVsExtensibility::RunWizardFile` metodę można wykonać przy użyciu nazwy zarejestrowanych kreatora lub identyfikator GUID i innych parametrów kontekstu, które IDE przekazuje do niego.  
  
## <a name="context-parameters-for-new-project"></a>Parametry kontekstu dla nowego projektu  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`WizardType`|Zarejestrowany typ kreatora (<xref:EnvDTE.Constants.vsWizardNewProject>) lub identyfikator GUID, który wskazuje na typ kreatora. W [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] {0F90E1D0-4999-11D1-B6D1-00A0C90F2744} jest implementacja, identyfikator GUID dla kreatora.|  
|`ProjectName`|Ciąg, który jest unikatowy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nazwy projektu.|  
|`LocalDirectory`|Lokalizacja lokalne pliki projektu pracy.|  
|`InstallationDirectory`|Ścieżka katalogu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest instalacja.|  
|`FExclusive`|Flaga wartości logicznej, co oznacza, że projekt, należy zamknąć otwarte rozwiązania.|  
|`SolutionName`|Nazwa pliku rozwiązania bez katalogu części lub rozszerzenia .sln. Nazwa pliku .suo również jest tworzony przy użyciu `SolutionName`. Jeśli ten argument nie jest ciągiem pustym, kreator używa <xref:EnvDTE._Solution.Create%2A> przed dodaniem projektu z <xref:EnvDTE._Solution.AddFromTemplate%2A>. Jeśli ta nazwa jest ciągiem pustym, użyj <xref:EnvDTE._Solution.AddFromTemplate%2A> bez wywoływania <xref:EnvDTE._Solution.Create%2A>.|  
|`Silent`|Wartość logiczna wskazująca, czy kreator powinien pracować w trybie dyskretnym tak, jakby **Zakończ** kliknięty (`TRUE`).|  
  
## <a name="context-parameters-for-add-new-item"></a>Parametry kontekstu Dodaj nowy element  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`WizardType`|Zarejestrowany typ kreatora (<xref:EnvDTE.Constants.vsWizardAddItem>) lub identyfikator GUID, który wskazuje na typ kreatora. W [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] {0F90E1D1-4999-11D1-B6D1-00A0C90F2744} jest implementacja, identyfikator GUID dla kreatora.|  
|`ProjectName`|Ciąg, który jest unikatowy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nazwy projektu.|  
|`ProjectItems`|Lokalizacja lokalna, który zawiera pliki projektu pracy.|  
|`ItemName`|Nazwa elementu, który ma zostać dodany. Ta nazwa jest domyślna nazwa pliku lub nazwę pliku, wpisywany przez użytkownika z **Dodaj elementy** okno dialogowe. Nazwa jest oparty na flagi, które są ustawione w pliku .vsdir. Nazwa może zawierać wartości null.|  
|`InstallationDirectory`|Ścieżka katalogu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest instalacja.|  
|`Silent`|Wartość logiczna wskazująca, czy kreator powinien pracować w trybie dyskretnym tak, jakby **Zakończ** kliknięty (`TRUE`).|  
  
## <a name="context-parameters-for-add-sub-project"></a>Parametry kontekstu dla projektu podrzędnego Dodaj  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`WizardType`|Zarejestrowany typ kreatora (<xref:EnvDTE.Constants.vsWizardAddSubProject>) lub identyfikator GUID, który wskazuje na typ kreatora. W [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] {0F90E1D2-4999-11D1-B6D1-00A0C90F2744} jest implementacja, identyfikator GUID dla kreatora.|  
|`ProjectName`|Ciąg, który jest unikatowy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nazwy projektu.|  
|`ProjectItems`|Wskaźnik do `ProjectItems` kolekcji, na którym działa Kreator. This, wskaźnik jest przekazywana do kreatora na podstawie pozycji wybranej hierarchii projektu. Użytkownik zwykle wybiera folder, w której ma zostać umieszczony element, a następnie wywołuje projektu **elementu Dodawanie** okno dialogowe.|  
|`LocalDirectory`|Lokalizacja lokalne pliki projektu pracy.|  
|`ItemName`|Nazwa elementu, który ma zostać dodany. Ta nazwa jest domyślna nazwa pliku lub nazwę pliku, wpisywany przez użytkownika z **Dodaj elementy** okno dialogowe. Nazwa jest oparty na flagi, które są ustawione w pliku .vsdir. Nazwa może zawierać wartości null.|  
|`InstallationDirectory`|Ścieżka katalogu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest instalacja.|  
|`Silent`|Wartość logiczna wskazująca, czy kreator powinien pracować w trybie dyskretnym tak, jakby **Zakończ** kliknięty (`TRUE`).|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)   
 [Kreatorzy](../../extensibility/internals/wizards.md)   
 [Kreator (. Plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Parametry kontekstu uruchomiania kreatorów](https://msdn.microsoft.com/library/051a10f4-9e45-4604-b344-123044f33a24)
