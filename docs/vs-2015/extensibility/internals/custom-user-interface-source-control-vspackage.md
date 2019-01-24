---
title: Niestandardowy interfejs użytkownika (pakiet VSPackage kontroli) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f03713213ec2e54ed8d82d7528dae12cefab7ebc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54757046"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Niestandardowy interfejs użytkownika (pakiet VSPackage kontroli kodu źródłowego)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakietu VSPackage deklaruje jego elementy menu i ich stany domyślny za pomocą pliku tabeli poleceń w usłudze Visual Studio (vsct). [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Zintegrowanego środowiska programistycznego (IDE) Wyświetla elementy menu w ich domyślnymi stanami, do momentu załadowania pakietu VSPackage. Następnie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda jest wywoływana, aby włączyć lub wyłączyć elementy menu.  
  
 Pakietu VSPackage można ustawić klucz rejestru, więc pakietu VSPackage mogą być ładowane automatycznie w zależności od kontekstu interfejsu użytkownika poleceń, chociaż zazwyczaj kontroli źródła pakietu VSPackage powinny zostać załadowane na żądanie, a nie po prostu przełączanie do określonego kontekstu interfejsu użytkownika. Aby uzyskać więcej informacji na temat klucza rejestru AutoLoadPackages zobacz [Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>VSPackage UI  
 Pakiet kontroli źródła jest zaimplementowany jako pakietu VSPackage i nie korzysta z interfejsu użytkownika z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Każdy formant źródła pakietu VSPackage, należy określić własne elementy interfejsu użytkownika, takie jak elementy menu, grupy menu, okien narzędzi, paski narzędzi i wszelkich wymaganych elementów interfejsu użytkownika dla ustawień dotyczących opcje pakietu VSPackage kontroli źródła. Te elementy interfejsu użytkownika można włączyć statycznie lub dynamicznie. Statyczne elementy interfejsu użytkownika są zdefiniowane w pliku vsct i są wyświetlane, czy pakietu VSPackage jest ładowany, czy nie. Dynamiczne elementy interfejsu użytkownika mogą być widoczne w zależności od określonego polecenia kontekstach interfejsu użytkownika, takie jak <xref:EnvDTE.Constants.vsContextNoSolution>, lub w wyniku wywołania <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody. Widoczność dynamicznych elementów interfejsu użytkownika jest zgodny z strategii opóźnionego ładowania pakietów VSPackage.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Ograniczenia interfejsu użytkownika w pakietach VSPackage kontroli źródła  
 Ponieważ nie można usunąć pakietu VSPackage kontroli źródła z poziomu środowiska IDE, po załadowaniu danych, pakietu VSPackage musi umożliwiać wprowadź nieaktywny. Gdy pakietu VSPackage otrzymuje powiadomienie, że nie jest już aktywna, pakietu VSPackage wyłącza jego interfejsu użytkownika i pomija interakcji z zewnętrznego środowiska IDE. Wykonanie pakietu VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody powinny Ukryj polecenia, gdy pakietu VSPackage nie jest aktywny.  
  
 Kontroli źródła, co należy zaimplementować pakietu VSPackage `IVsSccProvider` interfejsu. Dwie metody w interfejsie, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, muszą być zaimplementowane przez pakietu VSPackage.  
  
 Do kontroli źródła może masz subskrypcję pakietu VSPackage na różne zdarzenia IDE, które są implementowane przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>i tak dalej. Ponadto pakietu VSPackage mogą wdrażać włączone rejestru interfejsów wywołań zwrotnych, takich jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>. Te muszą wszystkich ignorowany podczas nieaktywne.  
  
 Na poniższej liście przedstawiono interfejsów wpływ aktywny stan pakietu VSPackage kontroli źródła:  
  
- Śledzenie zdarzeń dokumenty projektu.  
  
- Rozwiązanie zdarzenia.  
  
- Interfejsy stanu trwałego rozwiązania. Gdy nieaktywna, pakiety nie powinien zapisu .sln i .suo plików.  
  
- Właściwości rozszerzeń.  
  
  Wymagane <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, a także żadnych interfejsów opcjonalnie skojarzony z kontroli źródła nie są wywoływane, gdy pakietu VSPackage kontroli źródła jest nieaktywny.  
  
  Gdy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uruchamia IDE [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ustawia kontekst interfejsu użytkownika poleceń Identyfikator bieżącej kontroli źródła domyślny identyfikator pakietu VSPackage. Powoduje to statycznych interfejsu użytkownika formantu aktywne źródłowe pakietu VSPackage pojawią się w środowisku IDE bez faktycznego ładowania pakietu VSPackage. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Wstrzymuje dla pakietu VSPackage zarejestrować za pomocą [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> przed jego sprawia, że wszelkie wywołania do pakietu VSPackage.  
  
  W poniższej tabeli opisano konkretne szczegółowe informacje o tym, jak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE ukrywa różne elementy interfejsu użytkownika.  
  
|Element interfejsu użytkownika|Opis|  
|-------------|-----------------|  
|Menu i paski narzędzi|Pakiet kontroli źródła należy ustawić początkowych stanów widoczność menu i paski narzędzi do Identyfikatora pakietu kontroli źródła w [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) części pliku vsct. Dzięki temu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE odpowiednie ustawienie stanu elementów menu, bez konieczności ładowania pakietu VSPackage i wywoływania implementację <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody.|  
|Okna narzędzi|Kontrola źródła pakietu VSPackage ukrywa wszystkie okna narzędzi, który jest właścicielem, gdy staje się nieaktywna.|  
|Stronach opcji kontroli źródła specyficzne dla pakietu VSPackage|Klucz rejestru HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts umożliwia pakietu VSPackage ustawiania kontekstów, w których wymaga jego stron opcji mają być wyświetlane. Wpis rejestru, w tym kluczu musi być utworzony przy użyciu usługi identyfikator usługi kontroli źródła i przypisywanie jej wartość DWORD na 1. Zawsze, gdy wystąpi zdarzenie interfejsu użytkownika w kontekście kontroli źródła, które pakietu VSPackage jest zarejestrowane w usłudze, pakietu VSPackage zostanie wywołana, jeśli jest aktywny.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md)
