---
title: Parametry kontekstu | Microsoft Docs
description: Dowiedz się więcej o parametrach kontekstu Visual Studio zintegrowanym środowisku projektowym (IDE), które definiują stan projektu podczas dodawania lub implementowania kreatora.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 536e5abf92884c5c19399e73b4e1773e66919657
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898230"
---
# <a name="context-parameters"></a>Parametry kontekstu
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanym środowisku projektowym (IDE) można dodawać kreatory do okien dialogowych Nowy projekt, Dodaj nowy element lub Dodaj **projekt** podrzędny. Dodane kreatory są dostępne w menu **Plik** lub klikając prawym przyciskiem myszy projekt w **Eksplorator rozwiązań**. Ide przekazuje parametry kontekstu do implementacji kreatora. Parametry kontekstu definiują stan projektu, gdy idee wywołają kreatora.

 Ide uruchamia kreatorów, <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> ustawiając flagę w wywołaniu IDE metody dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> projektu. Po jego skonfigurowaniu projekt musi spowodować wykonanie metody przy użyciu nazwy lub identyfikatora GUID zarejestrowanego kreatora i innych parametrów kontekstu, które są do niego przekazuje `IVsExtensibility::RunWizardFile` idee.

## <a name="context-parameters-for-new-project"></a>Parametry kontekstu dla nowego projektu

| Parametr | Opis |
|-------------------------| - |
| `WizardType` | Typ zarejestrowanego kreatora () lub <xref:EnvDTE.Constants.vsWizardNewProject> identyfikator GUID wskazujący typ kreatora. W implementacji [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] identyfikator GUID kreatora to {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Ciąg, który jest unikatową [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nazwą projektu. |
| `LocalDirectory` | Lokalna lokalizacja plików projektu roboczego. |
| `InstallationDirectory` | Ścieżka katalogu to [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instalacja. |
| `FExclusive` | Flaga logiczna wskazująca, że projekt powinien zamknąć otwarte rozwiązania. |
| `SolutionName` | Nazwa pliku rozwiązania bez części katalogu lub *rozszerzenia sln.* Nazwa *pliku .suo* jest również tworzona przy `SolutionName` użyciu . Jeśli ten argument nie jest pustym ciągiem, kreator używa ciągu <xref:EnvDTE._Solution.Create%2A> przed dodaniem projektu za pomocą funkcji <xref:EnvDTE._Solution.AddFromTemplate%2A> . Jeśli ta nazwa jest pustym ciągiem, użyj <xref:EnvDTE._Solution.AddFromTemplate%2A> wartości bez wywoływania <xref:EnvDTE._Solution.Create%2A> . |
| `Silent` | Wartość logiczna wskazująca, czy kreator powinien działać w trybie dyskretnym, tak **jakby** kliknął przycisk Zakończ ( `TRUE` ). |

## <a name="context-parameters-for-add-new-item"></a>Parametry kontekstu dla dodawania nowego elementu

| Parametr | Opis |
|-------------------------| - |
| `WizardType` | Typ zarejestrowanego kreatora () lub <xref:EnvDTE.Constants.vsWizardAddItem> identyfikator GUID wskazujący typ kreatora. W implementacji [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] identyfikator GUID kreatora to {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Ciąg, który jest unikatową [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nazwą projektu. |
| `ProjectItems` | Lokalizacja lokalna zawierająca robocze pliki projektu. |
| `ItemName` | Nazwa elementu, który ma zostać dodany. Jest to domyślna nazwa pliku lub nazwa pliku, które użytkownik wpisze w oknie **dialogowym Dodawanie** elementów. Nazwa jest oparta na flagi, które są ustawione w *pliku vsdir.* Nazwa może być wartością null. |
| `InstallationDirectory` | Ścieżka katalogu to [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instalacja. |
| `Silent` | Wartość logiczna wskazująca, czy kreator powinien działać w trybie dyskretnym, tak **jakby** kliknął przycisk Zakończ ( `TRUE` ). |

## <a name="context-parameters-for-add-sub-project"></a>Parametry kontekstu dla dodawania projektu podrzędnego

| Parametr | Opis |
|-------------------------| - |
| `WizardType` | Typ zarejestrowanego kreatora () lub <xref:EnvDTE.Constants.vsWizardAddSubProject> identyfikator GUID wskazujący typ kreatora. W implementacji identyfikator GUID kreatora [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] to {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Ciąg, który jest unikatową [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nazwą projektu. |
| `ProjectItems` | Wskaźnik do `ProjectItems` kolekcji, na której działa kreator. Ten wskaźnik jest przekazywany do kreatora na podstawie wyboru hierarchii projektu. Użytkownik zazwyczaj wybiera folder, w którym ma być umieszczany element, a następnie wywołuje okno dialogowe Dodawanie **elementu** projektu. |
| `LocalDirectory` | Lokalna lokalizacja plików projektu roboczego. |
| `ItemName` | Nazwa elementu, który ma zostać dodany. Jest to domyślna nazwa pliku lub nazwa pliku, które użytkownik wpisze w oknie **dialogowym Dodawanie** elementów. Nazwa jest oparta na flagi, które są ustawione w *pliku vsdir.* Nazwa może być wartością null. |
| `InstallationDirectory` | Ścieżka katalogu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instalacji. |
| `Silent` | Wartość logiczna wskazująca, czy kreator powinien działać w trybie dyskretnym, tak **jakby** kliknął przycisk Zakończ ( `TRUE` ). |

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)
- [Kreatory](../../extensibility/internals/wizards.md)
- [Plik kreatora (vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Parametry kontekstu do uruchamiania kreatorów](/previous-versions/tz690efs(v=vs.140))