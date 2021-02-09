---
title: Niestandardowy interfejs użytkownika (pakietu VSPackage kontroli źródła) | Microsoft Docs
description: Dowiedz się, jak utworzyć niestandardowy interfejs użytkownika w programie Visual Studio za pomocą pakietu VSPackage kontroli źródła, aby określić elementy UI.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97c82254516c78a3aff9884e91e44adc45b95981
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902989"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Niestandardowy interfejs użytkownika (pakietu VSPackage kontroli źródła)
Pakietu VSPackage deklaruje elementy menu i ich domyślne Stany za pomocą pliku programu Visual Studio Command Table (*. vsct*). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Zintegrowane środowisko programistyczne (IDE) wyświetla elementy menu w ich domyślnych Stanach do momentu załadowania pakietu VSPackage. Następnie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Metoda jest wywoływana, aby włączyć lub wyłączyć elementy menu.

 Pakietu VSPackage może ustawić klucz rejestru, aby można było automatycznie załadować pakietu VSPackage w zależności od kontekstu interfejsu użytkownika (UI) polecenia, mimo że zwykle pakietu VSPackage kontroli źródła powinno ładować na żądanie, a nie tylko przełączać się do konkretnego kontekstu interfejsu użytkownika. Więcej informacji o kluczu rejestru **AutoLoadPackages** można znaleźć w temacie [Manage pakietów VSPackage](../../extensibility/managing-vspackages.md).

## <a name="vspackage-ui"></a>Interfejs użytkownika pakietu VSPackage
 Pakiet kontroli źródła jest implementowany jako pakietu VSPackage i nie korzysta z interfejsu użytkownika z programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Każdy pakietu VSPackage kontroli źródła musi określać własne elementy interfejsu użytkownika, takie jak elementy menu, grupy menu, okna narzędzi, paski narzędzi i każdy wymagany interfejs użytkownika do ustawiania opcji specyficznych dla pakietu VSPackage kontroli źródła. Te elementy interfejsu użytkownika można włączyć statycznie lub dynamicznie. Statyczne elementy interfejsu użytkownika są zdefiniowane w pliku *. vsct* i są wyświetlane niezależnie od tego, czy pakietu VSPackage jest załadowana, czy nie. Dynamiczne elementy interfejsu użytkownika mogą być widoczne w zależności od kontekstu interfejsu użytkownika polecenia, takiego jak <xref:EnvDTE.Constants.vsContextNoSolution> lub w wyniku wywołania <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody. Widoczność dynamicznych elementów interfejsu użytkownika jest zgodna z strategią opóźnionego ładowania pakietów VSPackage.

## <a name="ui-constraints-on-source-control-vspackages"></a>Ograniczenia interfejsu użytkownika dotyczące pakietów VSPackage kontroli źródła
 Ponieważ pakietu VSPackage kontroli źródła nie można usunąć z IDE po załadowaniu, pakietu VSPackage musi mieć możliwość wprowadzenia nieaktywnego stanu. Gdy pakietu VSPackage odbiera powiadomienie, że nie jest już aktywne, pakietu VSPackage wyłącza jego interfejs użytkownika i ignoruje wszelkie zewnętrzne interakcje IDE. Implementacja <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody pakietu VSPackage powinna ukrywać polecenia, gdy pakietu VSPackage nie jest aktywny.

 Każdy pakietu VSPackage kontroli źródła musi implementować `IVsSccProvider` interfejs. Dwie metody w interfejsie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> , muszą być implementowane przez pakietu VSPackage.

 Pakietu VSPackage kontroli źródła może mieć subskrypcję różnych zdarzeń IDE, które są implementowane przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> i tak dalej. Ponadto pakietu VSPackage mogą mieć zaimplementowane interfejsy wywołania zwrotnego z włączonym rejestrem, takie jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> . Wszystkie te interfejsy muszą być ignorowane, gdy są nieaktywne.

 Na poniższej liście przedstawiono interfejsy, których dotyczy stan aktywny pakietu VSPackage kontroli źródła:

- Śledź zdarzenia dokumentów projektu.

- Zdarzenia rozwiązania.

- Interfejsy trwałości rozwiązania. Gdy jest nieaktywny, pakiety nie powinny zapisywać w plikach *sln* i *. suo* .

- Rozszerzalność właściwości.

  Wymagane <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , a także wszelkie opcjonalne interfejsy skojarzone z kontrolą źródła nie są wywoływane, gdy pakietu VSPackage kontroli źródła jest nieaktywny.

  Po [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uruchomieniu IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ustawia kontekst interfejsu użytkownika polecenia na identyfikator bieżącego domyślnego identyfikatora pakietu VSPackage kontroli źródła. Powoduje to, że statyczny interfejs użytkownika aktywnej kontroli źródła pakietu VSPackage pojawia się w IDE bez faktycznego ładowania pakietu VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wstrzymuje działanie pakietu VSPackage, aby zarejestrować się w usłudze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] za pomocą programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> przed wykonaniem jakichkolwiek wywołań do pakietu VSPackage.

  W poniższej tabeli opisano szczegółowe informacje o tym, jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowisko IDE ukrywa różne elementy interfejsu użytkownika.

| Element interfejsu użytkownika | Opis |
| - | - |
| Menu i paski narzędzi | Pakiet kontroli źródła musi ustawić początkowe menu i Stany widoczności paska narzędzi na identyfikator pakietu kontroli źródła w sekcji [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) pliku *. vsct* . Dzięki temu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE może odpowiednio ustawić stan elementów menu bez ładowania pakietu VSPackage i wywoływania implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody. |
| Okna narzędzi | Pakietu VSPackage kontroli źródła ukrywa wszystkie okna narzędzi, które są własnością, gdy jest nieaktywny. |
| Strony opcji pakietu VSPackage kontroli źródła | Klucz rejestru **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts** umożliwia pakietu VSPackage Ustawianie kontekstów, w których będą wyświetlane strony opcji. Wpis rejestru w tym kluczu należy utworzyć przy użyciu identyfikatora usługi (SID) usługi kontroli źródła i przypisywania go do wartości DWORD 1. Za każdym razem, gdy w kontekście wystąpi zdarzenie pakietu VSPackage kontroli źródła, pakietu VSPackage zostanie wywołana, jeśli jest aktywny. |

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md)
