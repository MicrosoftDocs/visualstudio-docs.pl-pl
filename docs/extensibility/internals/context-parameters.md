---
title: Parametry kontekstu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ea38b79be362f78fcc34161a480597fb0ecce40
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727549"
---
# <a name="context-parameters"></a>Parametry kontekstu
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE) można dodać kreatory do okna dialogowego **Nowy projekt**, **Dodaj nowy element**lub **Dodaj projekt podrzędny** . Dodano kreatory dostępne w menu **plik** lub klikając prawym przyciskiem myszy projekt w **Eksplorator rozwiązań**. IDE przekazuje parametry kontekstu do implementacji kreatora. Parametry kontekstu definiują stan projektu, gdy IDE wywołuje kreatora.

 IDE uruchamia kreatory przez ustawienie flagi <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> w wywołaniu IDE wywołania metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> dla projektu. Po ustawieniu projekt musi spowodować wykonanie metody `IVsExtensibility::RunWizardFile` przy użyciu nazwy zarejestrowanego kreatora lub identyfikatora GUID oraz innych parametrów kontekstu, które IDE przekazuje do tego.

## <a name="context-parameters-for-new-project"></a>Parametry kontekstu dla nowego projektu

| Parametr | Opis |
|-------------------------| - |
| `WizardType` | Zarejestrowany typ kreatora (<xref:EnvDTE.Constants.vsWizardNewProject>) lub identyfikator GUID, który wskazuje typ kreatora. W implementacji [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] identyfikator GUID kreatora to {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Ciąg, który jest unikatową nazwą projektu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `LocalDirectory` | Lokalna lokalizacja roboczych plików projektu. |
| `InstallationDirectory` | Ścieżka katalogu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest instalacją. |
| `FExclusive` | Flaga logiczna wskazująca, że projekt powinien zamykać otwarte rozwiązania. |
| `SolutionName` | Nazwa pliku rozwiązania bez części katalogu lub rozszerzenia *sln* . Nazwa pliku *. suo* jest również tworzona przy użyciu `SolutionName`. Jeśli ten argument nie jest pustym ciągiem, Kreator użyje <xref:EnvDTE._Solution.Create%2A> przed dodaniem projektu z <xref:EnvDTE._Solution.AddFromTemplate%2A>. Jeśli ta nazwa jest pustym ciągiem, użyj <xref:EnvDTE._Solution.AddFromTemplate%2A> bez wywoływania <xref:EnvDTE._Solution.Create%2A>. |
| `Silent` | Wartość logiczna wskazująca, czy Kreator powinien działać w trybie dyskretnym, jeśli kliknięto przycisk **Zakończ** (`TRUE`). |

## <a name="context-parameters-for-add-new-item"></a>Parametry kontekstu dla dodawania nowego elementu

| Parametr | Opis |
|-------------------------| - |
| `WizardType` | Zarejestrowany typ kreatora (<xref:EnvDTE.Constants.vsWizardAddItem>) lub identyfikator GUID, który wskazuje typ kreatora. W implementacji [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] identyfikator GUID kreatora to {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Ciąg, który jest unikatową nazwą projektu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `ProjectItems` | Lokalizacja lokalna zawierająca pliki projektu roboczego. |
| `ItemName` | Nazwa elementu, który ma zostać dodany. Ta nazwa jest domyślną nazwą pliku lub nazwą pliku, który użytkownik wpisuje z okna dialogowego **Dodawanie elementów** . Nazwa jest oparta na flagach ustawionych w pliku *. vsdir* . Nazwa może być wartością null. |
| `InstallationDirectory` | Ścieżka katalogu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest instalacją. |
| `Silent` | Wartość logiczna wskazująca, czy Kreator powinien działać w trybie dyskretnym, jeśli kliknięto przycisk **Zakończ** (`TRUE`). |

## <a name="context-parameters-for-add-sub-project"></a>Parametry kontekstu dla dodawania projektu podrzędnego

| Parametr | Opis |
|-------------------------| - |
| `WizardType` | Zarejestrowany typ kreatora (<xref:EnvDTE.Constants.vsWizardAddSubProject>) lub identyfikator GUID, który wskazuje typ kreatora. W implementacji [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] identyfikator GUID kreatora to {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Ciąg, który jest unikatową nazwą projektu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `ProjectItems` | Wskaźnik do kolekcji `ProjectItems`, na której działa Kreator. Ten wskaźnik jest przesyłany do kreatora w oparciu o wybór hierarchii projektu. Użytkownik zwykle wybiera folder, w którym ma zostać umieszczony element, a następnie wywołuje okno dialogowe **Dodawanie elementu** projektu. |
| `LocalDirectory` | Lokalna lokalizacja roboczych plików projektu. |
| `ItemName` | Nazwa elementu, który ma zostać dodany. Ta nazwa jest domyślną nazwą pliku lub nazwą pliku, który użytkownik wpisuje z okna dialogowego **Dodawanie elementów** . Nazwa jest oparta na flagach ustawionych w pliku *. vsdir* . Nazwa może być wartością null. |
| `InstallationDirectory` | Ścieżka katalogu instalacji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `Silent` | Wartość logiczna wskazująca, czy Kreator powinien działać w trybie dyskretnym, jeśli kliknięto przycisk **Zakończ** (`TRUE`). |

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)
- [Kreatory](../../extensibility/internals/wizards.md)
- [Plik kreatora (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Parametry kontekstu do uruchamiania kreatorów](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)