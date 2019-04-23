---
title: Obsługa paska nawigacyjnego w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6cef18951a6ac5494f74c150c4251bafd9597686
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117944"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Obsługa paska nawigacyjnego w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pasek nawigacyjny u góry widoku edytora Wyświetla typy i elementy członkowskie w pliku. Typy są wyświetlane na liście rozwijanej po lewej stronie, a elementy członkowskie są wyświetlane w prawo rozwijanej. Gdy użytkownik wybierze typ, karetkę jest umieszczany w pierwszym wierszu tego typu. Gdy użytkownik wybierze element członkowski, karetkę jest umieszczany w definicji elementu członkowskiego. Pola listy rozwijanej, są aktualizowane zgodnie z bieżącym położeniem karetki.  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>Wyświetlanie i aktualizowanie pasek nawigacyjny  
 Aby zapewnić obsługę na pasku nawigacyjnym, należy wyprowadzić klasę z <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> klasę i zaimplementować <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody. Kiedy usługi języka otrzymuje okna kodu, base <xref:Microsoft.VisualStudio.Package.LanguageService> tworzy wystąpienie klasy <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, który zawiera <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> obiekt reprezentujący okno kodu. <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Nadano nowy obiekt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiektu. <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Metoda pobiera <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> obiektu. W przypadku zwrócenia wystąpienia usługi <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> klasy, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> wywołania usługi <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodę, aby wypełnić wewnętrzny zawiera listę i przekazuje swoje <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> do obiektu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] listę rozwijaną paska menedżera. Listę rozwijaną paska menedżera, z kolei wywołuje <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> metody w Twojej <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> obiektów do nawiązania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> obiekt, który zawiera dwa paski listy rozwijanej.  
  
 Kiedy przesuwa się daszek, <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> wywołania metody <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> metody. Podstawowy <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> wywołania metody <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> method in Class metoda swoje <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> klasy, aby zaktualizować stan na pasku nawigacyjnym. Przekaż zestaw <xref:Microsoft.VisualStudio.Package.DropDownMember> obiekty do tej metody. Każdy obiekt reprezentacja wpisu listy rozwijanej.  
  
## <a name="the-contents-of-the-navigation-bar"></a>Zawartość paska nawigacyjnego  
 Na pasku nawigacyjnym zwykle zawiera listę typów i listę elementów członkowskich. Lista typów obejmuje wszystkie typy dostępnych w bieżącym pliku źródłowym. Nazwy typów zawierają informacje pełną przestrzeni nazw. Oto przykładowy kod języka C# za pomocą dwóch typów:  
  
```csharp  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 Zostanie wyświetlona lista typów `TestLanguagePackage.TestLanguageService` i `TestLanguagePackage.TestLanguageService.Tokens`.  
  
 Lista elementów członkowskich Wyświetla dostępne elementy członkowskie tego typu, który jest zaznaczony na liście typów. Przy użyciu powyższego, przykładowy kod, jeśli `TestLanguagePackage.TestLanguageService` to typ, który jest zaznaczone, lista elementów członkowskich zawiera prywatne składowe `tokens` i `serviceName`. Struktury wewnętrznej `Token` nie jest wyświetlana.  
  
 Możesz zaimplementować listy elementów członkowskich do pogrubienie nazwę elementu członkowskiego, gdy karetkę jest umieszczony wewnątrz niego. Elementy Członkowskie mogą być także wyświetlane w wyszarzona tekstu, wskazujący, że nie znajdują się w zakresie, gdzie karetka jest ustawiana po raz obecnie.  
  
## <a name="enabling-support-for-the-navigation-bar"></a>Włączanie obsługi paska nawigacyjnego  
 Aby włączyć obsługę na pasku nawigacyjnym, należy ustawić `ShowDropdownBarOption` parametru <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybutu `true`. Ten parametr określa <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> właściwości. Aby zapewnić obsługę na pasku nawigacyjnym, należy zaimplementować <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> obiektu <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metody <xref:Microsoft.VisualStudio.Package.LanguageService> klasy.  
  
 W danej implementacji <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metody, jeśli <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> właściwość jest ustawiona na `true`, może zwrócić <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> obiektu. Jeśli nie zwraca obiektu, nie jest wyświetlana na pasku nawigacyjnym.  
  
 Można ustawić opcję, aby wyświetlać pasek nawigacyjny przez użytkownika, więc istnieje możliwość, że ta kontrolka do zresetowania przy otwartym widoku edytora. Użytkownik musi zamknąć i otworzyć okno edytora, przed wprowadzeniem zmiany.  
  
## <a name="implementing-support-for-the-navigation-bar"></a>Implementowanie obsługi paska nawigacyjnego  
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Metoda przyjmuje dwie listy (po jednym dla każdej listy rozwijanej) i dwie wartości reprezentujący bieżące zaznaczenie w każdej listy. Wartości wyboru i list mogą być aktualizowane, w którym to przypadku <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metoda musi zwracać `true` do wskazania, że listy zostały zmienione.  
  
 Jak zmieni się zaznaczenie w typach listy rozwijanej listy elementów członkowskich należy zaktualizować tak, aby odzwierciedlić nowego typu. Co to jest wyświetlany na liście elementów członkowskich mogą być:  
  
- Lista elementów członkowskich dla bieżącego typu.  
  
- Wszystkie elementy członkowskie dostępne w źródle pliku, ale przy użyciu wszystkich elementów członkowskich nie w bieżącym typem wyświetlane w tekście wyszarzona. Użytkownik może wybrać nadal członków wyszarzona, co umożliwia ich szybkie nawigowanie, ale kolor oznacza, że nie są częścią aktualnie wybranego typu.  
  
  Implementacja <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metoda przeważnie wykonuje następujące czynności:  
  
1. Zostanie wyświetlona lista bieżącej deklaracji dla pliku źródłowego.  
  
     Istnieją różne sposoby do wypełnienia listy. Jedno z podejść jest utworzenie niestandardowej metody na wersję <xref:Microsoft.VisualStudio.Package.LanguageService> klasy, która wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodę z powodu niestandardowych analizy, która zwraca listę wszystkich deklaracji. Innym rozwiązaniem może być wywołanie <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> bezpośrednio z metody <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodę z powodu niestandardowych analizy. Trzeci rozwiązaniem może być w pamięci podręcznej deklaracji w <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy zwrócony przez ostatnią pełną operację analizy w <xref:Microsoft.VisualStudio.Package.LanguageService> klasy i pobrać z <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody.  
  
2. Wypełnij lub zaktualizować listę typów.  
  
     Zawartość listy typów mogą zostać zaktualizowane po zmianie źródła lub jeśli zmiana stylu tekstu typów, w oparciu o bieżącym położeniu karetki. Należy zauważyć, że w tym miejscu jest przekazywany do <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody.  
  
3. Określ typ, wybierz z listy typów, oparte na bieżącym położeniu karetki.  
  
     Możesz wyszukać deklaracje, które zostały uzyskane w kroku 1, aby znaleźć typ, który otacza bieżącym położeniu karetki i następnie wyszukaj listę typów dla tego typu ustalić jego indeksu na liście typów.  
  
4. Wypełnij lub zaktualizować listę elementów członkowskich na podstawie wybranego typu.  
  
     Lista elementów członkowskich odzwierciedla, co to jest aktualnie wyświetlany w **członków** listy rozwijanej. Zawartość listy elementów członkowskich może być konieczne można zaktualizować, czy źródłowy został zmieniony, czy są wyświetlane tylko członkowie wybranego typu i wybrany typ został zmieniony. Jeśli wybierzesz wyświetlić wszystkie elementy członkowskie w pliku źródłowym, style tekstu poszczególnych członków na liście musi zostać zaktualizowany, jeśli aktualnie wybranego typu została zmieniona.  
  
5. Ustal, elementu członkowskiego, aby wybrać na liście elementów członkowskich na podstawie bieżącego położenia karetki.  
  
     Wyszukaj deklaracje, które zostały uzyskane w kroku 1 dla elementu członkowskiego, który zawiera bieżącym położeniu karetki, a następnie wyszukaj listę elementów członkowskich dla tego elementu, aby ustalić jego indeksu do listy członków.  
  
6. Zwróć `true` Jeśli zmiany zostały dokonane do listy lub zaznaczenia w obu list.
