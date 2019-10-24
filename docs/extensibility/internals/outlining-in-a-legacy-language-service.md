---
title: Tworzenie konspektu w starszej wersji usługi językowej | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6b2ba55a2e77a1f7261812a181ad780c2ef2b71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726177"
---
# <a name="outlining-in-a-legacy-language-service"></a>Zwijanie w starszej wersji usługi językowej
Konspekt umożliwia zwinięcie złożonego programu do przeglądu lub konspektu. Na przykład we C# wszystkich metodach można zwinąć do pojedynczego wiersza, pokazując tylko sygnaturę metody. Ponadto struktury i klasy mogą być zwinięte, aby pokazać tylko nazwy struktur i klas. Wewnątrz pojedynczej metody można zwinąć skomplikowaną logikę, aby pokazać ogólny przepływ, wyświetlając tylko pierwszy wiersz instrukcji, takich jak `foreach`, `if` i `while`.

 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [Przewodnik: Tworzenie konspektu](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.

## <a name="enabling-support-for-outlining"></a>Włączanie obsługi konspektu
 Wpis rejestru `AutoOutlining` ma wartość 1, aby włączyć automatyczne tworzenie konspektu. Automatyczne tworzenie konspektu ustawia analizę całego źródła, gdy plik zostanie załadowany lub zmieniony w celu zidentyfikowania ukrytych regionów i pokazania symboli konspektu. Konspekt można również kontrolować ręcznie przez użytkownika.

 Wartość wpisu rejestru `AutoOutlining` można uzyskać za pomocą właściwości <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> klasy <xref:Microsoft.VisualStudio.Package.LanguagePreferences>. Wpis rejestru `AutoOutlining` można zainicjować przy użyciu nazwanego parametru do atrybutu <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> (zobacz [Rejestrowanie starszej wersji usługi językowej,](../../extensibility/internals/registering-a-legacy-language-service1.md) Aby uzyskać szczegółowe informacje).

## <a name="the-hidden-region"></a>Ukryty region
 Aby zapewnić tworzenie konspektów, usługa języka musi obsługiwać ukryte regiony. Są to zakresy tekstu, które mogą być rozwinięte lub zwinięte. Ukryte regiony mogą być rozdzielone symbolami języka standardowego, takimi jak nawiasy klamrowe, lub według symboli niestandardowych. Na przykład C# ma `#region` / `#endregion` para, która ogranicza ukryty region.

 Ukryte regiony są zarządzane przez Menedżera ukrytych regionów, który jest udostępniany jako interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>.

 Tworzenie konspektu używa ukrytych regionów interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> i zawiera zakres ukrytego regionu, bieżący widoczny stan oraz transparent, który ma być wyświetlany, gdy zasięg jest zwinięty.

 Analizator usługi językowej używa metody <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A>, aby dodać nowy ukryty region z zachowaniem domyślnym dla ukrytych regionów, podczas gdy metoda <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> umożliwia dostosowanie wyglądu i zachowania konspektu. Po przydzieleniu ukrytych regionów do sesji ukrytego obszaru program [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zarządza ukrytymi regionami usługi językowej.

 Jeśli konieczne jest określenie, kiedy sesja ukrytego regionu zostanie zniszczona, ukryty region jest zmieniany lub trzeba upewnić się, że określony ukryty region jest widoczny; należy utworzyć klasę z klasy <xref:Microsoft.VisualStudio.Package.Source> i odpowiednio zastąpić odpowiednie metody, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> i <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>.

### <a name="example"></a>Przykład
 Poniżej przedstawiono uproszczony przykład tworzenia ukrytych regionów dla wszystkich par nawiasów klamrowych. Przyjęto założenie, że język zawiera dopasowanie nawiasów klamrowych i że nawiasy klamrowe mają być dopasowane, zawierają co najmniej nawiasy klamrowe ({i}). Takie podejście służy wyłącznie do celów informacyjnych. Pełna implementacja będzie miała pełną obsługę przypadków w <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. Ten przykład pokazuje również, jak ustawić preferencję <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A>, aby `true` czasowo. Alternatywą jest określenie `AutoOutlining` nazwanego parametru w atrybucie `ProvideLanguageServiceAttribute` w pakiecie językowym.

 W tym przykładzie C# założono reguły dotyczące komentarzy, ciągów i literałów.

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

## <a name="see-also"></a>Zobacz także
- [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)
- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)