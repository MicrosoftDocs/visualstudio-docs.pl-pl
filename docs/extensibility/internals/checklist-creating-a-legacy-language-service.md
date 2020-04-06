---
title: 'Lista kontrolna: Tworzenie usługi języka starszego | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11785dab63cbb6a95ab2d34c5edbfb4525ebf34c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709786"
---
# <a name="checklist-create-a-legacy-language-service"></a>Lista kontrolna: tworzenie starszej usługi językowej
Na poniższej liście kontrolnej podsumowano podstawowe kroki, które należy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wykonać, aby utworzyć usługę językową dla edytora podstawowego. Aby zintegrować usługę [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]języka z programem , należy utworzyć oceniającego wyrażenie debugowania. Aby uzyskać więcej informacji, zobacz [Pisanie ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) w [rozciągliwości debugera programu Visual Studio.](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

## <a name="steps-to-create-a-language-service"></a>Kroki tworzenia usługi językowej

1. Zaimplementuj interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.

    - W vspackage zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfejs, aby zapewnić usługę języka.

    - Udostępnij usługę języka zintegrowanemu środowisku programistycznemu (IDE) w implementacji. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>

2. Zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfejs w klasie usługi języka głównego.

     Interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> jest punktem wyjścia interakcji między edytorem podstawowym a usługą językową.

### <a name="optional-features"></a>Funkcje opcjonalne
 Następujące funkcje są opcjonalne i mogą być implementowane w dowolnej kolejności. Te funkcje zwiększają funkcjonalność usługi językowej.

- Kolorowanie składni

  Zaimplementuj interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. Implementacja tego interfejsu powinna informacje analizatora, aby zwrócić odpowiednie informacje o kolorze.

  Metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> zwraca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejs. Oddzielne wystąpienie colorizer jest tworzony dla każdego buforu tekstu, więc należy zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejs oddzielnie. Aby uzyskać więcej informacji, zobacz [Kolorowanie składni w starszej usłudze językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).

- Okno Kod

  Zaimplementuj interfejs, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> aby umożliwić usługi języka, aby otrzymywać powiadomienia o utworzeniu nowego okna kodu.

  Metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> zwraca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfejs. Usługa języka może następnie dodać specjalny interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>użytkownika do okna kodu w pliku . Usługa językowa może również wykonywać wszelkie specjalne przetwarzanie, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>takie jak dodawanie filtru widoku tekstu w pliku .

- Filtr widoku tekstu

  Aby zapewnić zakończenie instrukcji IntelliSense w usłudze języka, należy przechwycić niektóre polecenia, które w przeciwnym razie obsłużyłby widok tekstu. Aby przechwycić te polecenia, wykonaj następujące czynności:

  - Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> do udziału w łańcuchu poleceń i obsługi poleceń edytora.

  - Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodę i <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> przekaż w implementacji.

  - Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> metody po odłączeniu od widoku, tak aby te polecenia nie są już przekazywane do Ciebie.

  Polecenia, które muszą być obsługiwane, zależą od świadczonych usług. Aby uzyskać więcej informacji, zobacz [Ważne polecenia dotyczące filtrów usług językowych](../../extensibility/internals/important-commands-for-language-service-filters.md).

  > [!NOTE]
  > Interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> musi być zaimplementowany <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> na tym samym obiekcie co interfejs.

- Uzupełnianie oświadczenia

  Zaimplementuj interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.

  Obsługa polecenia uzupełniania instrukcji <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>(czyli ) <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> wywołaj metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> w interfejsie, przekazując interfejs. Aby uzyskać więcej informacji, zobacz [Uzupełnianie instrukcji w starszej usłudze języka](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).

- Porady dotyczące metod

  Zaimplementuj interfejs, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> aby zapewnić dane dla okna końcówki metody.

  Zainstaluj filtr widoku tekstu, aby odpowiednio obsługiwać polecenia, aby wiedzieć, kiedy wyświetlić okno poradki o danych metody. Aby uzyskać więcej informacji, zobacz [Informacje o parametrach w starszej usłudze języka](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).

- Znaczniki błędów

  Zaimplementuj interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.

  Utwórz obiekty znacznika <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> błędu, które <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> implementują <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejs i wywołają metodę, przekazując interfejs obiektu znacznika błędu.

  Zazwyczaj każdy znacznik błędu zarządza elementem w oknie listy zadań.

- Elementy listy zadań

  Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> klasę elementu zadania zapewniającą interfejs.

  Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> klasę dostawcy <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> zadań zapewniającą interfejs i interfejs.

  Zaimplementuj klasę modułu wyliczania zadań zapewniającą <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> interfejs.

  Zarejestruj dostawcę zadań przy za <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> pomocą metody listy zadań.

  Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfejs, dzwoniąc do dostawcy usług językowych z <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>identyfikatorem GUID usługi .

  Utwórz obiekty elementu <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> zadania i <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> wywołaj metodę w interfejsie, gdy istnieją nowe lub zaktualizowane zadania.

- Elementów zadania komentarz

  Użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfejsu i <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfejsu, aby uzyskać tokeny zadania komentarza.

  Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfejs z <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> usługi.

  Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfejs z <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> metody.

  Zaimplementuj interfejs, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> aby nasłuchiwać zmian na liście tokenów.

- Tworzenie konspektu

  Istnieje kilka opcji obsługi nakreślenia. Na przykład można obsługiwać **zwijanie do definicji** polecenia, zapewnić regiony konspektu kontrolowane przez edytora lub obsługiwać regiony kontrolowane przez klienta. Aby uzyskać więcej informacji, zobacz [Jak: Zapewnienie rozszerzonej obsługi nakreślania w starszej usłudze językowej](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).

- Rejestracja usługi językowej

  Aby uzyskać więcej informacji na temat rejestrowania usługi językowej, zobacz [Rejestrowanie starszej usługi językowej](../../extensibility/internals/registering-a-legacy-language-service2.md) i [Zarządzanie pakietami VSPackages](../../extensibility/managing-vspackages.md).

- Pomoc kontekstowa

  Podaj kontekst edytorowi w jeden z następujących sposobów:

  - Podaj kontekst znaczników tekstu, implementując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfejs.

  - Podaj cały kontekst <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> użytkownika, implementując interfejs.

## <a name="see-also"></a>Zobacz też
- [Tworzenie starszej usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Napisz ewaluatora wyrażenia CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
