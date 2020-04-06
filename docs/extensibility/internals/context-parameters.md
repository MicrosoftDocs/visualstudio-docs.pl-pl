---
title: Parametry kontekstu | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709310"
---
# <a name="context-parameters"></a>Parametry kontekstu
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanym środowisku programistycznym (IDE) można dodawać kreatory do okien dialogowych **Nowy projekt**, **Dodawanie nowego elementu**lub Dodawanie projektu **podrzędnego.** Dodane kreatory są dostępne w menu **Plik** lub po kliknięciu prawym przyciskiem myszy projektu w **Eksploratorze rozwiązań**. IDE przekazuje parametry kontekstu do implementacji kreatora. Parametry kontekstu definiują stan projektu, gdy IDE wywołuje kreatora.

 IDE uruchamia kreatorów, ustawiając flagę <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> w wywołaniu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> IDE do metody dla projektu. Po ustawieniu projektu musi `IVsExtensibility::RunWizardFile` spowodować, że metoda ma być wykonana przy użyciu nazwy zarejestrowanego kreatora lub identyfikatora GUID i innych parametrów kontekstu, które IDE przekazuje do niego.

## <a name="context-parameters-for-new-project"></a>Parametry kontekstu dla nowego projektu

| Parametr | Opis |
|-------------------------| - |
| `WizardType` | Zarejestrowany typ<xref:EnvDTE.Constants.vsWizardNewProject>kreatora ( ) lub identyfikator GUID wskazujący typ kreatora. W [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementacji identyfikator GUID kreatora to {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Ciąg, który jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unikatową nazwą projektu. |
| `LocalDirectory` | Lokalna lokalizacja roboczych plików projektu. |
| `InstallationDirectory` | Ścieżka katalogu jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instalacja. |
| `FExclusive` | Flaga logiczna wskazująca, że projekt powinien zamknąć otwarte rozwiązania. |
| `SolutionName` | Nazwa pliku rozwiązania bez części katalogu lub rozszerzenia *.sln.* Nazwa pliku *.suo* jest również `SolutionName`tworzona przy użyciu programu . Jeśli ten argument nie jest pustym <xref:EnvDTE._Solution.Create%2A> ciągiem, kreator <xref:EnvDTE._Solution.AddFromTemplate%2A>używa przed dodaniem projektu z programem . Jeśli ta nazwa jest pustym ciągiem, użyj <xref:EnvDTE._Solution.AddFromTemplate%2A> bez wywoływania <xref:EnvDTE._Solution.Create%2A>. |
| `Silent` | Wartość logiczna wskazująca, czy kreator powinien działać w`TRUE`trybie cichym, tak jakby kliknięno przycisk **Zakończ** ( ). |

## <a name="context-parameters-for-add-new-item"></a>Parametry kontekstu dla dodaj nowy element

| Parametr | Opis |
|-------------------------| - |
| `WizardType` | Zarejestrowany typ<xref:EnvDTE.Constants.vsWizardAddItem>kreatora ( ) lub identyfikator GUID wskazujący typ kreatora. W [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementacji identyfikator GUID kreatora to {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Ciąg, który jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unikatową nazwą projektu. |
| `ProjectItems` | Lokalizacja lokalna zawierająca robocze pliki projektu. |
| `ItemName` | Nazwa elementu, który ma zostać dodany. Ta nazwa jest domyślną nazwą pliku lub nazwą pliku wpisywanymi przez użytkownika w oknie dialogowym **Dodawanie elementów.** Nazwa jest oparta na flagi, które są ustawione w pliku *vsdir.* Nazwa może być wartością null. |
| `InstallationDirectory` | Ścieżka katalogu jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instalacja. |
| `Silent` | Wartość logiczna wskazująca, czy kreator powinien działać w`TRUE`trybie cichym, tak jakby kliknięno przycisk **Zakończ** ( ). |

## <a name="context-parameters-for-add-sub-project"></a>Parametry kontekstu dla dodaj projekt podrzędny

| Parametr | Opis |
|-------------------------| - |
| `WizardType` | Zarejestrowany typ<xref:EnvDTE.Constants.vsWizardAddSubProject>kreatora ( ) lub identyfikator GUID wskazujący typ kreatora. W [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementacji identyfikator GUID kreatora to {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Ciąg, który jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unikatową nazwą projektu. |
| `ProjectItems` | Wskaźnik do `ProjectItems` kolekcji, na której działa kreator. Ten wskaźnik jest przekazywany do kreatora na podstawie wyboru hierarchii projektu. Użytkownik zazwyczaj wybiera folder, w którym ma umieścić element, a następnie wywołuje okno dialogowe **Dodawanie elementu** projektu. |
| `LocalDirectory` | Lokalna lokalizacja roboczych plików projektu. |
| `ItemName` | Nazwa elementu, który ma zostać dodany. Ta nazwa jest domyślną nazwą pliku lub nazwą pliku wpisywanymi przez użytkownika w oknie dialogowym **Dodawanie elementów.** Nazwa jest oparta na flagi, które są ustawione w pliku *vsdir.* Nazwa może być wartością null. |
| `InstallationDirectory` | Ścieżka katalogu instalacji. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] |
| `Silent` | Wartość logiczna wskazująca, czy kreator powinien działać w`TRUE`trybie cichym, tak jakby kliknięno przycisk **Zakończ** ( ). |

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)
- [Kreatory](../../extensibility/internals/wizards.md)
- [Plik Kreatora (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Parametry kontekstu uruchamiania kreatorów](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
