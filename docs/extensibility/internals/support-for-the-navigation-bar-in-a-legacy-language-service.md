---
title: Obsługa paska nawigacyjnego w starszej usłudze językowej | Dokumenty firmy Microsoft
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
ms.openlocfilehash: f86dabb0594b1e33c45808efb387fcbe313e3de3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704863"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Obsługa paska nawigacyjnego w starszej wersji usługi językowej
Pasek nawigacyjny w górnej części widoku edytora wyświetla typy i elementy członkowskie w pliku. Typy są wyświetlane w lewym rozwijaniu, a elementy członkowskie są wyświetlane w prawym rozwijaniu. Gdy użytkownik wybierze typ, cieszka jest umieszczana w pierwszym wierszu typu. Gdy użytkownik wybierze element członkowski, opieki jest umieszczana w definicji elementu członkowskiego. Rozwijane pola są aktualizowane w celu odzwierciedlenia bieżącej lokalizacji cieszy.

## <a name="displaying-and-updating-the-navigation-bar"></a>Wyświetlanie i aktualizowanie paska nawigacyjnego
 Aby obsługiwać pasek nawigacyjny, należy wyprowadzić <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> klasę z <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> klasy i zaimplementować metodę. Gdy usługa języka otrzymuje okno kodu, <xref:Microsoft.VisualStudio.Package.LanguageService> klasa podstawowa <xref:Microsoft.VisualStudio.Package.CodeWindowManager>wystąpienia , <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> który zawiera obiekt reprezentujący okno kodu. Obiekt <xref:Microsoft.VisualStudio.Package.CodeWindowManager> otrzymuje nowy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiekt. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> pobiera <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> obiekt. Jeśli zwrócisz wystąpienie <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> klasy, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> wywoła <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodę wypełniania wewnętrznych list i <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> przekazuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obiekt do menedżera listy rozwijanej. Menedżer rozwijany pasek z kolei wywołuje <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> metodę <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> na obiekcie, aby ustanowić <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> obiekt, który posiada dwa paski rozwijane.

 Gdy przesunie <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> się cieszka, metoda wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> metodę. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> podstawowa <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> wywołuje metodę <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> w klasie, aby zaktualizować stan paska nawigacyjnego. Zestaw <xref:Microsoft.VisualStudio.Package.DropDownMember> obiektów należy przekazać do tej metody. Każdy obiekt reprezentuje wpis z listy rozwijanej.

## <a name="the-contents-of-the-navigation-bar"></a>Zawartość paska nawigacyjnego
 Pasek nawigacyjny zwykle zawiera listę typów i listę członków. Lista typów zawiera wszystkie typy dostępne w bieżącym pliku źródłowym. Nazwy typów zawierają pełne informacje o obszarze nazw. Poniżej przedstawiono przykład kodu C# z dwoma typami:

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

 Zostanie wyświetlona `TestLanguagePackage.TestLanguageService` lista `TestLanguagePackage.TestLanguageService.Tokens`typów i .

 Na liście członków są wyświetlane dostępne elementy członkowskie typu wybranego na liście typów. Korzystając z powyższego `TestLanguagePackage.TestLanguageService` przykładu kodu, jeśli jest to typ, `tokens` który `serviceName`jest zaznaczony, lista członków będzie zawierać członków prywatnych i . Struktura `Token` wewnętrzna nie jest wyświetlana.

 Można zaimplementować listę członków, aby nazwa elementu członkowskiego pogrubiona, gdy daszka jest umieszczona wewnątrz niego. Elementy członkowskie mogą być również wyświetlane w wyszarzonych tekstach, co oznacza, że nie znajdują się w zakresie, w którym znajduje się obecnie cieszka.

## <a name="enabling-support-for-the-navigation-bar"></a>Włączanie obsługi paska nawigacyjnego
 Aby włączyć obsługę paska nawigacyjnego, <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> należy ustawić `true` `ShowDropdownBarOption` parametr atrybutu na . Ten parametr <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> ustawia właściwość. Aby obsługiwać pasek nawigacyjny, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> należy zaimplementować obiekt w metodzie <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> w <xref:Microsoft.VisualStudio.Package.LanguageService> klasie.

 W implementacji <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metody, jeśli <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> właściwość `true`jest ustawiona <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> na , można zwrócić obiekt. Jeśli obiekt nie zostanie zwracany, pasek nawigacyjny nie zostanie wyświetlony.

 Opcja wyświetlania paska nawigacyjnego może być ustawiona przez użytkownika, dzięki czemu można zresetować ten formant, gdy widok edytora jest otwarty. Użytkownik musi zamknąć i ponownie otworzyć okno edytora przed zmianą.

## <a name="implementing-support-for-the-navigation-bar"></a>Wdrażanie obsługi paska nawigacyjnego
 Metoda <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> przyjmuje dwie listy (po jednej dla każdej listy rozwijanej) i dwie wartości reprezentujące bieżący wybór na każdej liście. Listy i wartości wyboru mogą być aktualizowane, w którym to przypadku <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metoda musi powrócić, `true` aby wskazać, że listy uległy zmianie.

 W miarę zmiany zaznaczenia w rozwijanych typach lista członków musi zostać zaktualizowana w celu odzwierciedlenia nowego typu. To, co jest pokazane na liście członków, może być następujące:

- Lista elementów członkowskich dla bieżącego typu.

- Wszystkie elementy członkowskie dostępne w pliku źródłowym, ale wszystkie elementy członkowskie nie w bieżącym typie wyświetlane w wyszarzonych tekstach. Użytkownik nadal może wybrać wyszarzone elementy członkowskie, dzięki czemu mogą być używane do szybkiej nawigacji, ale kolor wskazuje, że nie są one częścią aktualnie wybranego typu.

  Implementacja <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody zazwyczaj wykonuje następujące kroki:

1. Pobierz listę bieżących deklaracji dla pliku źródłowego.

     Istnieje wiele sposobów wypełniania list. Jednym z podejść jest utworzenie metody <xref:Microsoft.VisualStudio.Package.LanguageService> niestandardowej w <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> wersji klasy, która wywołuje metodę z powodu analizy niestandardowej, która zwraca listę wszystkich deklaracji. Innym podejściem może <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> być wywołanie <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody bezpośrednio z metody z powodu analizy niestandardowej. Trzecie podejście może być do pamięci <xref:Microsoft.VisualStudio.Package.AuthoringScope> podręcznej deklaracji w klasie zwrócone <xref:Microsoft.VisualStudio.Package.LanguageService> przez ostatnią pełną operację <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> analizy w klasie i pobrać, że z metody.

2. Wypełnij lub zaktualizuj listę typów.

     Zawartość listy typów może zostać zaktualizowana po zmianie źródła lub w przypadku zmiany stylu tekstu typów na podstawie bieżącej pozycji daszka. Należy zauważyć, że ta <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> pozycja jest przekazywana do metody.

3. Określ typ do wyboru na liście typów na podstawie bieżącego stanowiska cieszy.

     Można przeszukiwać deklaracje, które zostały uzyskane w kroku 1, aby znaleźć typ, który otacza bieżącą pozycję daterii, a następnie przeszukać listę typów dla tego typu, aby określić jego indeks na liście typów.

4. Wypełnij lub zaktualizuj listę elementów członkowskich na podstawie wybranego typu.

     Lista członków odzwierciedla to, co jest obecnie wyświetlane w liście rozwijanej **Członkowie.** Zawartość listy członków może wymagać aktualizacji, jeśli źródło uległo zmianie lub jeśli wyświetlane są tylko elementy członkowskie wybranego typu i wybrany typ uległ zmianie. Jeśli wybierzesz wyświetlanie wszystkich elementów członkowskich w pliku źródłowym, styl tekstu każdego członka na liście musi zostać zaktualizowany, jeśli aktualnie wybrany typ uległ zmianie.

5. Określ członka, który ma być wybierany na liście członków na podstawie bieżącego stanowiska cieszy.

     Przeszukaj deklaracje, które zostały uzyskane w kroku 1 dla elementu członkowskiego, który zawiera bieżącą pozycję opiekuna, a następnie przeszukaj listę członków dla tego członka, aby określić jego indeks na liście elementów członkowskich.

6. Wróć, `true` jeśli wprowadzono jakiekolwiek zmiany na listach lub w których zostały wprowadzone zaznaczenia na dowolnej liście.
