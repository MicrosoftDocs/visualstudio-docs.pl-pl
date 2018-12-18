---
title: 'Lista kontrolna: Tworzenie starszej wersji usługi językowej | Dokumentacja firmy Microsoft'
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
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 330270b34d55e88c883b9d8a6270b4abad02d9c1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782989"
---
# <a name="checklist-creating-a-legacy-language-service"></a>Lista kontrolna: tworzenie starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poniższa lista zawiera podsumowanie podstawowe kroki, które należy wykonać, aby można było utworzyć language service Pro [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] edytorze podstawowych funkcji. Aby zintegrować usługi w języka [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], należy utworzyć ewaluatora wyrażeń debugowania. Aby uzyskać więcej informacji, zobacz [pisanie ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) w [rozszerzeń debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="steps-for-creating-a-language-service"></a>Procedury służące do tworzenia usługi językowej  
  
1.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interfejsu.  
  
    -   W pliku z pakietu VSPackage, zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfejsu, aby zapewnić obsługę języka.  
  
    -   Udostępnianie usługi w języka zintegrowanego środowiska programistycznego (IDE) w swojej <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementacji.  
  
2.  Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfejsu w klasie usługi główny język.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Interfejs jest punktem początkowym interakcji między podstawowy edytor i usługa językowa.  
  
### <a name="optional-features"></a>Funkcje opcjonalne  
 Następujące funkcje są opcjonalne i może być implementowany w dowolnej kolejności. Te funkcje zwiększyć funkcjonalność usługi języka.  
  
- Kolorowanie składni  
  
   Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejsu. Implementacja tego interfejsu powinny informacji analizatora, aby zostały zwrócone informacje odpowiedni kolor.  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Metoda zwraca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejsu. Wystąpienie oddzielnych colorizer nie jest tworzone dla każdego bufora tekstowego powinny implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejsu oddzielnie. Aby uzyskać więcej informacji, zobacz [kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
- W oknie kodu  
  
   Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfejsu, aby włączyć usługę języka otrzymać powiadomienie o po utworzeniu nowego okna kodu.  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> Metoda zwraca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfejsu. Usługa językowa można następnie dodać specjalne interfejsu użytkownika do okna kodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>. Usługa językowa można również wykonać jakiegokolwiek przetwarzania specjalne, takie jak dodanie filtru widoku tekstu w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.  
  
- Filtr widoku tekstu  
  
   Aby zapewnić instrukcji IntelliSense w ramach usługi w języka, przechwycić niektórych poleceń, które widoku tekstu w przeciwnym razie będzie obsługiwać. Aby przechwytywać te polecenia, wykonaj następujące czynności:  
  
  - Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> do wzięcia udziału w poleceń edytora łańcucha i obsługują polecenia.  
  
  - Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody i przekazać w swojej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementacji.  
  
  - Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> metoda po odłączeniu z widoku tak, że te polecenia są już przekazywane.  
  
    Polecenia, które muszą być obsługiwane są zależne od usług, które są dostarczane. Aby uzyskać więcej informacji, zobacz [ważne polecenia dotyczące filtrów usługi językowej](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
  > [!NOTE]
  >  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Interfejs musi zostać wdrożone na tym samym obiekcie jako <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu.  
  
- Uzupełnianie instrukcji  
  
   Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfejsu.  
  
   Obsługuje polecenia uzupełniania instrukcji (oznacza to, że <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) i wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> method in Class metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsu, przekazując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfejsu. Aby uzyskać więcej informacji, zobacz [uzupełnianie instrukcji w starszej wersji usługi językowej](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
- Wskazówki — metoda  
  
   Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfejsu, aby dostarczać dane dla metody okno porad.  
  
   Filtr widoku tekstu do obsługi poleceń, należy zainstalować, dzięki czemu będzie wiadomo, kiedy mają być wyświetlane okno porad do danych — metoda. Aby uzyskać więcej informacji, zobacz [o parametrach w starszej wersji usługi językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
- Znaczniki błędów  
  
   Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu.  
  
   Błąd podczas tworzenia obiektów znaczników, które implementują <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu i wywołania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> jest metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejs obiektu znacznika błędu.  
  
   Każdy znacznik błąd zarządza zwykle element okno listy zadań.  
  
- Elementy listy zadań  
  
   Implementowanie, zapewniając klasy elementu zadania <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> interfejsu.  
  
   Implementowanie, zapewniając klasy dostawcy zadań <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> interfejsu i <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> interfejsu.  
  
   Implementowanie, zapewniając klasy modułu wyliczającego zadanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> interfejsu.  
  
   Zarejestruj dostawcę zadań z listy zadań <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> metody.  
  
   Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfejsu, wywołując usługi językowej dostawcy usług w usłudze GUID <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.  
  
   Tworzenie obiektów elementów zadań, a następnie wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> method in Class metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfejs, gdy istnieją nowe lub zaktualizowane zadania.  
  
- Komentarz elementów zadań  
  
   Użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfejsu i <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfejs do uzyskiwania komentarz tokenów zadania.  
  
   Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfejs z <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> usługi.  
  
   Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfejs z <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> metody.  
  
   Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> interfejs do nasłuchiwania zmian na liście tokenów.  
  
- Tworzenie konspektu  
  
   Dostępnych jest kilka opcji do obsługi konspektu. Na przykład, może obsługiwać **Zwiń do definicji** polecenia, podaj kontrolowane przez Edytor konspektu regionów lub obsługuje regionów kontrolowane przez klienta. Aby uzyskać więcej informacji, zobacz [jak: Podaj rozwinięte konspekt pomocy technicznej w starszej wersji usługi językowej](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
- Rejestracja usługi w języka  
  
   Aby uzyskać więcej informacji o tym, jak zarejestrować usługi języka, zobacz [rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service2.md) i [Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md).  
  
- Pomoc kontekstowa  
  
   Podaj kontekstu do edytora w jednym z następujących sposobów:  
  
  -   Dostarczanie kontekstu znaczników tekstu poprzez implementację <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfejsu.  
  
  Podaj wszystkie kontekstu użytkownika poprzez implementację <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Pisanie ewaluatora wyrażeń środowiska CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

