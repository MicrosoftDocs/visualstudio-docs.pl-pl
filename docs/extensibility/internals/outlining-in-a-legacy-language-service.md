---
title: Tworzenie nakreślenia w starszej usłudze językowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be485a0e7406d49c4dcce77958c720e0b62504b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706808"
---
# <a name="outlining-in-a-legacy-language-service"></a>Zwijanie w starszej wersji usługi językowej
Konspekt umożliwia zwinięcie złożonego programu w przegląd lub konspekt. Na przykład w języku C# wszystkie metody mogą być zwinięte do pojedynczego wiersza, pokazując tylko podpis metody. Ponadto struktury i klasy mogą być zwinięte, aby wyświetlić tylko nazwy struktur i klas. Wewnątrz pojedynczej metody złożona logika może być zwinięty, aby pokazać `foreach`ogólny `if`przepływ, pokazując tylko pierwszy wiersz instrukcji, takich jak , i `while`.

 Starsze usługi języka są implementowane jako część VSPackage, ale nowszym sposobem implementowania funkcji usługi języka jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [Przewodnik: Nakreślanie](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Zaleca się, aby rozpocząć korzystanie z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i umożliwi korzystanie z nowych funkcji edytora.

## <a name="enabling-support-for-outlining"></a>Włączanie obsługi tworzenia wykreślenia
 Wpis `AutoOutlining` rejestru jest ustawiony na 1, aby włączyć automatyczne tworzenie nakreślenia. Automatyczne konspekt konspekt konspektuje analizę całego źródła, gdy plik jest ładowany lub zmieniany w celu zidentyfikowania ukrytych regionów i wyświetlenia glifów konspekcyjnych. Tworzenie nakreślenia może być również kontrolowane ręcznie przez użytkownika.

 Wartość wpisu `AutoOutlining` rejestru można uzyskać <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> za pośrednictwem <xref:Microsoft.VisualStudio.Package.LanguagePreferences> właściwości w klasie. Wpis `AutoOutlining` rejestru można zainicjować za pomocą <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> nazwanego parametru do atrybutu (zobacz [Rejestrowanie usługi języka starszego,](../../extensibility/internals/registering-a-legacy-language-service1.md) aby uzyskać szczegółowe informacje).

## <a name="the-hidden-region"></a>Ukryty region
 Aby zapewnić tworzenie nakreślenia, usługa języka musi obsługiwać ukryte regiony. Są to zakresy tekstu, które można rozwinąć lub zwinąć. Ukryte regiony mogą być rozdzielane przez standardowe symbole językowe, takie jak nawiasy klamrowe lub symbole niestandardowe. Na przykład C# `#region` / `#endregion` ma parę, która wyznacza ukryty region.

 Ukryte regiony są zarządzane przez menedżera regionu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> ukrytych, który jest narażony jako interfejs.

 Tworzenie obliczeń używa ukrytych <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> regionów interfejsu i zawiera zakres ukrytego regionu, bieżący stan widoczny i baner, który ma być wyświetlany, gdy zakres jest zwinięty.

 Analizator usługi języka używa <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metody, aby dodać nowy ukryty region z domyślnym <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> zachowaniem dla ukrytych regionów, podczas gdy metoda umożliwia dostosowanie wyglądu i zachowania konspektu. Po wprowadzeniu ukrytych regionów do ukrytej sesji regionu zarządza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ukrytymi regionami dla usługi językowej.

 Jeśli musisz określić, kiedy ukryta sesja regionu zostanie zniszczona, ukryty region zostanie zmieniony lub musisz upewnić się, że widoczny jest określony ukryty region; należy wyprowadzić klasę z <xref:Microsoft.VisualStudio.Package.Source> klasy i zastąpić odpowiednie <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>metody, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, i , odpowiednio.

### <a name="example"></a>Przykład
 Oto uproszczony przykład tworzenia ukrytych regionów dla wszystkich par nawiasów klamrowych. Zakłada się, że język zapewnia dopasowywanie nawiasów klamrowych i że nawiasy klamrowe, które mają być dopasowane, zawierają co najmniej nawiasy klamrowe ({ i }). Takie podejście ma charakter wyłącznie ilustracyjne. Pełne wdrożenie miałoby pełne rozpatrywanie <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>spraw w . W tym przykładzie pokazano <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> również, jak ustawić preferencję `true` tymczasowo. Alternatywą jest określenie `AutoOutlining` nazwanego `ProvideLanguageServiceAttribute` parametru w atrybucie w pakiecie językowym.

 W tym przykładzie przyjęto założenie, że reguły języka C# dla komentarzy, ciągów i literałów.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{

    public class MyLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences  GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(MyLanguageService).GUID,
                                                        Name);
                m_preferences.Init();
                // Temporarily enabled auto-outlining
                m_preferences.AutoOutlining = true;
            }
            return m_preferences;
        }

        public override AuthoringScope  ParseSource(ParseRequest req)
        {
            Source source = (Source) this.GetSource(req.FileName);
            switch (req.Reason)
            {
               case ParseReason.HighlightBraces:
               case ParseReason.MatchBraces:
               case ParseReason.MemberSelectAndHighlightBraces:
                  if (source.Braces != null)
                  {
                      foreach (TextSpan[] brace in source.Braces)
                      {
                         if (brace.Length == 2)
                         {
                             if (req.Sink.HiddenRegions == true
                                   && source.GetText(brace[0]).Equals("{")
                                   && source.GetText(brace[1]).Equals("}"))
                             {
                                //construct a TextSpan of everything between the braces
                                TextSpan hideSpan = new TextSpan();
                                hideSpan.iStartIndex = brace[0].iStartIndex;
                                hideSpan.iStartLine = brace[0].iStartLine;
                                hideSpan.iEndIndex = brace[1].iEndIndex;
                                hideSpan.iEndLine = brace[1].iEndLine;
                                req.Sink.ProcessHiddenRegions = true;
                                req.Sink.AddHiddenRegion(hideSpan);
                             }
                             req.Sink.MatchPair(brace[0], brace[1], 1);
                         }
                         else if (brace.Length >= 3)
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);
                  }
        }
                   break;
               default:
                   break;
      }
            // Must always return a valid AuthoringScope object.
            return new MyAuthoringScope();
        }
    }
}
```

## <a name="see-also"></a>Zobacz też
- [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)
- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)
