---
title: Niestandardowy interfejs użytkownika (kontrola źródła VSPackage) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6ef807cef17a6ca3cddfee05ba57ace27e34a9e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708928"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Niestandardowy interfejs użytkownika (formant źródła VSPackage)
VsPackage deklaruje swoje elementy menu i ich stany domyślne za pośrednictwem pliku polecenia programu Visual Studio (*.vsct).* Zintegrowane [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowisko programistyczne (IDE) wyświetla elementy menu w ich stanach domyślnych, dopóki nie zostanie załadowany vspackage. Następnie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda jest wywoływana, aby włączyć lub wyłączyć elementy menu.

 VSPackage można ustawić klucz rejestru, dzięki czemu VSPackage mogą być automatycznie ładowane w zależności od kontekstu interfejsu użytkownika polecenia (UI), chociaż zazwyczaj formantu źródła VSPackage należy załadować na żądanie, a nie tylko przełączanie do określonego kontekstu interfejsu użytkownika. Aby uzyskać więcej informacji na temat klucza rejestru **AutoLoadPackages,** zobacz [Zarządzanie pakietami VSPackages](../../extensibility/managing-vspackages.md).

## <a name="vspackage-ui"></a>Interfejs użytkownika pakietu VSPackage
 Pakiet kontroli źródła jest implementowany jako VSPackage i nie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]używa żadnego interfejsu użytkownika z . Każdy formant źródła VSPackage musi określić własne elementy interfejsu użytkownika, takie jak elementy menu, grupy menu, okna narzędzi, paski narzędzi i wszelkie wymagane interfejsu użytkownika do ustawiania opcji specyficznych dla formantu źródła VSPackage. Te elementy interfejsu użytkownika można włączyć statycznie lub dynamicznie. Statyczne elementy interfejsu użytkownika są zdefiniowane w pliku *vsct* i są wyświetlane, czy VSPackage jest załadowany, czy nie. Elementy interfejsu użytkownika dynamicznego mogą być widoczne w zależności <xref:EnvDTE.Constants.vsContextNoSolution>od kontekstu interfejsu użytkownika określonego <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> polecenia, takiego jak , lub w wyniku wywołania metody. Widoczność dynamicznych elementów interfejsu użytkownika jest zgodna ze strategią opóźnionego ładowania pakietów VSPackages.

## <a name="ui-constraints-on-source-control-vspackages"></a>Ograniczenia interfejsu użytkownika w formancie źródła VSPackages
 Ponieważ formantu źródła VSPackage nie można usunąć z IDE po załadowaniu, VSPackage musi być w stanie wprowadzić stan nieaktywny. Gdy VSPackage odbiera powiadomienie, że nie jest już aktywny, VSPackage wyłącza jego interfejsu użytkownika i ignoruje wszelkie zewnętrzne interakcji IDE. VsPackage implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody należy ukryć polecenia, gdy VSPackage nie jest aktywny.

 Każdy formant źródła VSPackage musi implementować `IVsSccProvider` interfejs. Dwie metody w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> interfejsie i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, muszą być zaimplementowane przez VSPackage.

 Formant źródła VSPackage może subskrybować różne zdarzenia IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>które są implementowane przez , i tak dalej. Ponadto VSPackage może zaimplementować interfejsy wywołania zwrotnego <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>z włączoną funkcją rejestru, takie jak . Wszystkie te interfejsy muszą być ignorowane, gdy są nieaktywne.

 Na poniższej liście przedstawiono interfejsy, których dotyczy aktywny stan formantu źródła VSPackage:

- Śledzenie zdarzeń dokumentów projektu.

- Zdarzenia rozwiązania.

- Interfejsy trwałości rozwiązania. Gdy pakiety są nieaktywne, nie powinny być zapisywane w plikach *.sln* i *.suo.*

- Przedłużacze właściwości.

  Wymagane <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, a także wszystkie opcjonalne interfejsy skojarzone z kontrolą źródła, nie są wywoływane, gdy formant źródła VSPackage jest nieaktywny.

  Po [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uruchomieniu IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ustawia kontekst interfejsu użytkownika polecenia na identyfikator bieżącego domyślnego formantu źródła VSPackage ID. Powoduje to, że statyczny interfejs użytkownika kontrolki aktywnego źródła VSPackage pojawiają się w IDE bez faktycznie ładowania VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pauzuje dla VSPackage zarejestrować [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> się za pośrednictwem przed sprawia, że wszelkie wywołania VSPackage.

  W poniższej tabeli opisano [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] szczegółowe informacje o tym, jak IDE ukrywa różne elementy interfejsu użytkownika.

| Element interfejsu użytkownika | Opis |
| - | - |
| Menu i paski narzędzi | Pakiet kontroli źródła musi ustawić początkowe menu i stany widoczności paska narzędzi na identyfikator pakietu kontroli źródła w sekcji [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) pliku *.vsct.* Dzięki temu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, aby ustawić stan elementów menu odpowiednio bez ładowania VSPackage i wywołanie implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody. |
| Okna narzędzi | Formant źródła VSPackage ukrywa wszystkie okna narzędzia, które posiada, gdy jest nieaktywny. |
| Strony opcji specyficzne dla formantu źródła VSPackage | Klucz rejestru **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts** umożliwia programowi VSPackage ustawienie kontekstów, w których wymaga wyświetlania stron opcji. Wpis rejestru pod tym kluczem musiałby zostać utworzony przy użyciu identyfikatora usługi (SID) usługi kontroli źródła i przydzieleniu jej wartości DWORD 1. Za każdym razem, gdy zdarzenie interfejsu użytkownika występuje w kontekście kontroli źródła VSPackage jest zarejestrowany, VSPackage zostanie wywołana, jeśli jest aktywny. |

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md)
