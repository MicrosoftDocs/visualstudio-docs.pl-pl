---
title: Obsługa paska nawigacyjnego w starszej wersji usługi językowej
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f22aaf552cc69074c500508621ab4d9e288ef449
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741905"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Obsługa paska nawigacyjnego w starszej wersji usługi językowej
Pasek nawigacyjny w górnej części widoku edytora wyświetla typy i elementy członkowskie w pliku. Typy są wyświetlane na liście rozwijanej po lewej stronie, a elementy członkowskie są wyświetlane na liście rozwijanej po prawej stronie. Gdy użytkownik wybierze typ, karetka zostanie umieszczona w pierwszym wierszu typu. Gdy użytkownik wybierze element członkowski, karetka zostanie umieszczona na definicji elementu członkowskiego. Pola rozwijane są aktualizowane w celu odzwierciedlenia bieżącej lokalizacji karetki.

## <a name="displaying-and-updating-the-navigation-bar"></a>Wyświetlanie i aktualizowanie paska nawigacyjnego
 Aby obsłużyć pasek nawigacyjny, należy utworzyć klasę klasy z <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> klasy i zaimplementować <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodę. Gdy usługa językowa otrzymuje okno kodu, <xref:Microsoft.VisualStudio.Package.LanguageService> Klasa bazowa tworzy wystąpienie elementu <xref:Microsoft.VisualStudio.Package.CodeWindowManager> , który zawiera <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> obiekt reprezentujący okno kodu. <xref:Microsoft.VisualStudio.Package.CodeWindowManager>Obiekt uzyskuje nowy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiekt. <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>Metoda pobiera <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> obiekt. Jeśli zwracasz wystąpienie <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> klasy, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> wywołuje <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodę w celu wypełnienia list wewnętrznych i przekazuje <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> obiekt do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Menedżera pasków listy rozwijanej. Menedżer paska listy rozwijanej, z kolei wywołuje <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> metodę w <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> obiekcie, aby określić <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> obiekt, który zawiera dwa paski rozwijane.

 Gdy karetka przesuwa się, <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> Metoda wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> metodę. Metoda bazowa <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> wywołuje <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodę w <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> klasie w celu zaktualizowania stanu paska nawigacyjnego. Przekazanie zestawu <xref:Microsoft.VisualStudio.Package.DropDownMember> obiektów do tej metody. Każdy obiekt reprezentuje wpis na liście rozwijanej.

## <a name="the-contents-of-the-navigation-bar"></a>Zawartość paska nawigacyjnego
 Pasek nawigacyjny zawiera zwykle listę typów i listę elementów członkowskich. Lista typów zawiera wszystkie typy dostępne w bieżącym pliku źródłowym. Nazwy typów obejmują pełne informacje o przestrzeni nazw. Poniżej przedstawiono przykładowy kod w języku C# z dwoma typami:

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

 Zostanie wyświetlona lista typów `TestLanguagePackage.TestLanguageService` i `TestLanguagePackage.TestLanguageService.Tokens` .

 Lista członków wyświetla dostępne elementy członkowskie typu, który został wybrany z listy typy. Korzystając z powyższego przykładu kodu, jeśli `TestLanguagePackage.TestLanguageService` jest wybrany typ, Lista członków będzie zawierać prywatne elementy członkowskie `tokens` i `serviceName` . Struktura wewnętrzna `Token` nie jest wyświetlana.

 Można zaimplementować listę elementów członkowskich, aby nazwa elementu członkowskiego była pogrubiona, gdy znak daszka jest umieszczony wewnątrz. Elementy członkowskie mogą być również wyświetlane w kolorze szarym, co oznacza, że nie znajdują się w zakresie, w którym karetka jest obecnie ustawiona.

## <a name="enabling-support-for-the-navigation-bar"></a>Włączanie obsługi paska nawigacyjnego
 Aby włączyć obsługę paska nawigacyjnego, należy ustawić `ShowDropdownBarOption` parametr <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybutu na `true` . Ten parametr ustawia <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> Właściwość. Aby obsługiwać pasek nawigacyjny, należy zaimplementować <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> obiekt w <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metodzie <xref:Microsoft.VisualStudio.Package.LanguageService> klasy.

 W implementacji <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metody, jeśli <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> Właściwość jest ustawiona na `true` , można zwrócić <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> obiekt. Jeśli obiekt nie zostanie zwrócony, pasek nawigacyjny nie zostanie wyświetlony.

 Opcja wyświetlania paska nawigacyjnego może zostać ustawiona przez użytkownika, więc można ją zresetować, gdy widok edytora jest otwarty. Użytkownik musi zamknąć i ponownie otworzyć okno edytora przed wprowadzeniem zmiany.

## <a name="implementing-support-for-the-navigation-bar"></a>Implementowanie obsługi paska nawigacyjnego
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>Metoda przyjmuje dwie listy (po jednej dla każdej listy rozwijanej) i dwie wartości reprezentujące bieżące zaznaczenie na każdej z nich. Listy i wartości wyboru można aktualizować, w tym przypadku <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Metoda musi powrócić, `true` Aby wskazać, że listy uległy zmianie.

 Po zmianie zaznaczenia na liście rozwijanej typy należy zaktualizować listę elementów członkowskich, aby odzwierciedlała nowy typ. Elementy wyświetlane na liście składowe mogą być następujące:

- Lista elementów członkowskich bieżącego typu.

- Wszystkie elementy członkowskie dostępne w pliku źródłowym, ale ze wszystkimi elementami członkowskimi, których nie ma w bieżącym typie wyświetlanych w tekście szarym. Użytkownik może nadal wybierać wyszarzone elementy członkowskie, aby można było ich użyć do szybkiej nawigacji, ale kolor wskazuje, że nie są one częścią aktualnie wybranego typu.

  Implementacja <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody zwykle wykonuje następujące czynności:

1. Pobierz listę bieżących deklaracji dla pliku źródłowego.

     Istnieją różne sposoby wypełniania list. Jednym z metod jest utworzenie niestandardowej metody w swojej wersji <xref:Microsoft.VisualStudio.Package.LanguageService> klasy, która wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodę z niestandardowym przyczyną analizy, która zwraca listę wszystkich deklaracji. Innym rozwiązaniem może być wywołanie <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody bezpośrednio z <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody z niestandardowym przyczyną analizy. Trzecie podejście może być w pamięci podręcznej deklaracji w <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasie zwracanej przez ostatnią pełną operację analizy w <xref:Microsoft.VisualStudio.Package.LanguageService> klasie i pobrać ją z <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody.

2. Wypełnij lub zaktualizuj listę typów.

     Zawartość listy typów może zostać zaktualizowana, gdy źródło uległo zmianie lub jeśli wybrano zmianę stylu tekstu typów na podstawie bieżącego położenia karetki. Należy zauważyć, że ta pozycja jest przenoszona do <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody.

3. Określ typ, który ma zostać wybrany na liście typów na podstawie bieżącego położenia karetki.

     Można wyszukać deklaracje, które zostały uzyskane w kroku 1, aby znaleźć typ, który zawiera bieżącą pozycję karetki, a następnie przeszukać listę typów dla tego typu, aby określić swój indeks na liście typów.

4. Wypełnij lub zaktualizuj listę elementów członkowskich na podstawie wybranego typu.

     Lista członków odzwierciedla elementy, które są aktualnie wyświetlane na liście rozwijanej **Członkowie** . Zawartość listy członków może wymagać aktualizacji, jeśli źródło zostało zmienione lub jeśli są wyświetlane tylko elementy członkowskie wybranego typu, a wybrany typ został zmieniony. Jeśli wybierzesz opcję wyświetlania wszystkich elementów członkowskich w pliku źródłowym, należy zaktualizować style tekstu każdego elementu członkowskiego na liście, jeśli aktualnie wybrany typ został zmieniony.

5. Określ element członkowski do wyboru na liście członków na podstawie bieżącego położenia karetki.

     Przeszukaj deklaracje, które zostały uzyskane w kroku 1 dla elementu członkowskiego, który zawiera bieżącą pozycję karetki, a następnie przeszukaj listę elementów członkowskich dla tego elementu członkowskiego, aby określić jego indeks na liście elementów członkowskich.

6. Zwróć, `true` Jeśli wprowadzono jakiekolwiek zmiany na listach lub wybrane z nich.
