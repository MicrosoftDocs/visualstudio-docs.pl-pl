---
title: 'Lista kontrolna: Tworzenie starszej wersji usługi językowej | Microsoft Docs'
description: Poznaj podstawowe kroki, które należy wykonać, aby utworzyć starszą wersję usługi językowej dla edytora podstawowego programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 823d46453ac6ad4a1a5a42c1f7d18a079b39d12d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905858"
---
# <a name="checklist-create-a-legacy-language-service"></a>Lista kontrolna: Tworzenie starszej wersji usługi językowej
Poniższa lista kontrolna zawiera podsumowanie podstawowych kroków, które należy wykonać w celu utworzenia usługi językowej dla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] edytora podstawowego. Aby zintegrować usługę języka z usługą [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , musisz utworzyć ewaluatora wyrażeń debugowania. Aby uzyskać więcej informacji, zobacz [pisanie ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) w [rozszerzalności debugera Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="steps-to-create-a-language-service"></a>Procedura tworzenia usługi języka

1. Zaimplementuj interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.

    - W pakietu VSPackage Zaimplementuj interfejs w <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> celu zapewnienia usługi językowej.

    - Udostępnienie usługi językowej dla zintegrowanego środowiska programistycznego (IDE) w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementacji.

2. Zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfejs w klasie głównej usługi językowej.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>Interfejs jest punktem początkowym interakcji między edytorem podstawowym a usługą języka.

### <a name="optional-features"></a>Funkcje opcjonalne
 Następujące funkcje są opcjonalne i mogą być implementowane w dowolnej kolejności. Te funkcje zwiększają funkcjonalność usługi językowej.

- Kolorowanie składni

  Zaimplementuj interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. Twoja implementacja tego interfejsu powinna mieć informacje o analizatorze, aby zwracały odpowiednie informacje o kolorach.

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>Metoda zwraca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejs. Dla każdego buforu tekstu tworzone jest oddzielne wystąpienie kolorowania, dlatego należy zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejs osobno. Aby uzyskać więcej informacji, zobacz [kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).

- Okno kodu

  Zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfejs, aby umożliwić usłudze języka otrzymywanie powiadomień o utworzeniu nowego okna kodu.

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>Metoda zwraca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfejs. Usługa języka może następnie dodać specjalny interfejs użytkownika do okna kod w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> . Usługa języka może również wykonywać wszelkie specjalne przetwarzanie, takie jak Dodawanie filtru widoku tekstu w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A> .

- Filtr widoku tekstu

  Aby zapewnić uzupełnianie instrukcji IntelliSense w usłudze językowej, należy przechwycić niektóre polecenia, które w przeciwnym razie mógłby obsłużyć widok tekstu. Aby przechwycić te polecenia, wykonaj następujące czynności:

  - Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , aby wziąć udział w łańcuchu poleceń i obsłużyć polecenia edytora.

  - Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodę i przekaż swoją <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementację.

  - Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> metodę po odłączeniu się do widoku, aby te polecenia nie były już przesyłane do Ciebie.

  Polecenia, które muszą być obsługiwane, zależą od usług, które są dostarczane. Aby uzyskać więcej informacji, zobacz [Ważne polecenia dla filtrów usługi językowej](../../extensibility/internals/important-commands-for-language-service-filters.md).

  > [!NOTE]
  > <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>Interfejs musi być zaimplementowany w tym samym obiekcie co <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs.

- Uzupełnianie instrukcji

  Zaimplementuj interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.

  Obsługuj polecenie uzupełniania instrukcji (czyli <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> ) i Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodę w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsie, przekazując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfejs. Aby uzyskać więcej informacji, zobacz [uzupełnianie instrukcji w starszej wersji usługi językowej](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).

- Porady dotyczące metod

  Zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfejs, aby zapewnić dane dla okna etykietki metody.

  Zainstaluj filtr widoku tekstu, aby odpowiednio obsługiwać polecenia, więc wiesz, kiedy pokazać okno etykietki danych metody. Aby uzyskać więcej informacji, zobacz [Informacje o parametrach w starszej wersji usługi językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).

- Znaczniki błędów

  Zaimplementuj interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.

  Utwórz obiekty znacznika błędu implementujące <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejs i Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metodę, przekazując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejs obiektu znacznika błędu.

  Zwykle każdy znacznik błędu zarządza elementem w oknie Lista zadań.

- Elementy listy zadań

  Zaimplementuj klasę elementu zadania dostarczającą <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> interfejs.

  Zaimplementuj klasę dostawcy zadań dostarczającą <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> interfejs i <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> interfejs.

  Zaimplementuj klasę modułu wyliczającego zadania dostarczającą <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> interfejs.

  Zarejestruj dostawcę zadań przy użyciu metody listy zadań <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> .

  Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfejs, wywołując dostawcę usług w usłudze języka z identyfikatorem GUID usługi <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> .

  Utwórz obiekty elementów zadania i Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> metodę w <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfejsie, jeśli są nowe lub zaktualizowane zadania.

- Komentarze elementów zadania

  Użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfejsu i interfejsu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> Aby uzyskać tokeny zadania komentarza.

  Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfejs z <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> usługi.

  Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfejs przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> metody.

  Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> interfejs, aby nasłuchiwać zmian na liście tokenów.

- Tworzenie konspektu

  Istnieje kilka opcji obsługi konspektu. Można na przykład obsłużyć polecenie **Zwiń do definicji** , udostępnić regiony konspektu z kontrolą edytora lub obsługiwać regiony kontrolowane przez klienta. Aby uzyskać więcej informacji, zobacz [How to: zapewnianie rozszerzonej obsługi konspektu w starszej wersji usługi językowej](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).

- Rejestracja usługi językowej

  Aby uzyskać więcej informacji na temat rejestrowania usługi językowej, zobacz [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service2.md) i [Zarządzanie pakietów VSPackage](../../extensibility/managing-vspackages.md).

- Pomoc kontekstowa

  Udostępnij kontekst dla edytora w jeden z następujących sposobów:

  - Podaj kontekst dla znaczników tekstowych przez implementację <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfejsu.

  - Podaj wszystkie konteksty użytkownika przez implementację <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfejsu.

## <a name="see-also"></a>Zobacz też
- [Opracowywanie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Napisz ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
