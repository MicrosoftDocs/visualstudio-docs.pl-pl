---
title: Parametry kontekstu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6673ad8f26c94165635b5f1bc652b91dcbbfd24f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709310"
---
# <a name="context-parameters"></a>Parametry kontekstu
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanym środowisku programistycznym (IDE) można dodać kreatorów do okna dialogowego **Nowy projekt**, **Dodaj nowy element**lub **Dodaj projekt podrzędny** . Dodano kreatory dostępne w menu **plik** lub klikając prawym przyciskiem myszy projekt w **Eksplorator rozwiązań**. IDE przekazuje parametry kontekstu do implementacji kreatora. Parametry kontekstu definiują stan projektu, gdy IDE wywołuje kreatora.

 IDE uruchamia kreatory przez ustawienie <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> flagi w WYWOŁANIU IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metody dla projektu. Po ustawieniu projekt musi spowodować `IVsExtensibility::RunWizardFile` wykonanie metody przy użyciu nazwy zarejestrowanego kreatora lub identyfikatora GUID oraz innych parametrów kontekstu, które IDE przekazuje do tego.

## <a name="context-parameters-for-new-project"></a>Parametry kontekstu dla nowego projektu

| Parametr | Opis |
|-------------------------| - |
| `WizardType` | Zarejestrowany typ kreatora ( <xref:EnvDTE.Constants.vsWizardNewProject> ) lub identyfikator GUID, który wskazuje typ kreatora. W [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementacji identyfikator GUID kreatora to {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Ciąg, który jest unikatową [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nazwą projektu. |
| `LocalDirectory` | Lokalna lokalizacja roboczych plików projektu. |
| `InstallationDirectory` | Ścieżka katalogu programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest instalacją. |
| `FExclusive` | Flaga logiczna wskazująca, że projekt powinien zamykać otwarte rozwiązania. |
| `SolutionName` | Nazwa pliku rozwiązania bez części katalogu lub rozszerzenia *sln* . Nazwa pliku *. suo* jest również tworzona przy użyciu `SolutionName` . Gdy ten argument nie jest pustym ciągiem, Kreator używa <xref:EnvDTE._Solution.Create%2A> przed dodaniem projektu z <xref:EnvDTE._Solution.AddFromTemplate%2A> . Jeśli ta nazwa jest pustym ciągiem, użyj <xref:EnvDTE._Solution.AddFromTemplate%2A> bez wywoływania metody <xref:EnvDTE._Solution.Create%2A> . |
| `Silent` | Wartość logiczna wskazująca, czy Kreator powinien działać w trybie dyskretnym, tak **jakby zostało** kliknięte ( `TRUE` ). |

## <a name="context-parameters-for-add-new-item"></a>Parametry kontekstu dla dodawania nowego elementu

| Parametr | Opis |
|-------------------------| - |
| `WizardType` | Zarejestrowany typ kreatora ( <xref:EnvDTE.Constants.vsWizardAddItem> ) lub identyfikator GUID, który wskazuje typ kreatora. W [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementacji identyfikator GUID kreatora to {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Ciąg, który jest unikatową [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nazwą projektu. |
| `ProjectItems` | Lokalizacja lokalna zawierająca pliki projektu roboczego. |
| `ItemName` | Nazwa elementu, który ma zostać dodany. Ta nazwa jest domyślną nazwą pliku lub nazwą pliku, który użytkownik wpisuje z okna dialogowego **Dodawanie elementów** . Nazwa jest oparta na flagach ustawionych w pliku *. vsdir* . Nazwa może być wartością null. |
| `InstallationDirectory` | Ścieżka katalogu programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest instalacją. |
| `Silent` | Wartość logiczna wskazująca, czy Kreator powinien działać w trybie dyskretnym, tak **jakby zostało** kliknięte ( `TRUE` ). |

## <a name="context-parameters-for-add-sub-project"></a>Parametry kontekstu dla dodawania projektu podrzędnego

| Parametr | Opis |
|-------------------------| - |
| `WizardType` | Zarejestrowany typ kreatora ( <xref:EnvDTE.Constants.vsWizardAddSubProject> ) lub identyfikator GUID, który wskazuje typ kreatora. W [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementacji identyfikator GUID kreatora to {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Ciąg, który jest unikatową [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nazwą projektu. |
| `ProjectItems` | Wskaźnik do `ProjectItems` kolekcji, w której działa Kreator. Ten wskaźnik jest przesyłany do kreatora w oparciu o wybór hierarchii projektu. Użytkownik zwykle wybiera folder, w którym ma zostać umieszczony element, a następnie wywołuje okno dialogowe **Dodawanie elementu** projektu. |
| `LocalDirectory` | Lokalna lokalizacja roboczych plików projektu. |
| `ItemName` | Nazwa elementu, który ma zostać dodany. Ta nazwa jest domyślną nazwą pliku lub nazwą pliku, który użytkownik wpisuje z okna dialogowego **Dodawanie elementów** . Nazwa jest oparta na flagach ustawionych w pliku *. vsdir* . Nazwa może być wartością null. |
| `InstallationDirectory` | Ścieżka katalogu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instalacji. |
| `Silent` | Wartość logiczna wskazująca, czy Kreator powinien działać w trybie dyskretnym, tak **jakby zostało** kliknięte ( `TRUE` ). |

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)
- [Kreatory](../../extensibility/internals/wizards.md)
- [Plik kreatora (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Parametry kontekstu do uruchamiania kreatorów](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
