---
title: Tworzenie konspektu w starszej wersji usługi językowej | Microsoft Docs
description: Dowiedz się, jak obsługiwać tworzenie konspektów przez implementację ukrytych regionów w starszej wersji usługi językowej.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ca457c32751fb1f9179a9c09b624c444efab627d
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876837"
---
# <a name="outlining-in-a-legacy-language-service"></a>Zwijanie w starszej wersji usługi językowej
Konspekt umożliwia zwinięcie złożonego programu do przeglądu lub konspektu. Na przykład w języku C# wszystkie metody można zwinąć do pojedynczego wiersza, pokazując tylko sygnaturę metody. Ponadto struktury i klasy mogą być zwinięte, aby pokazać tylko nazwy struktur i klas. Wewnątrz pojedynczej metody można zwinąć skomplikowaną logikę, aby pokazać ogólny przepływ, pokazując tylko pierwszy wiersz instrukcji, takich jak `foreach` , `if` , i `while` .

 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [Przewodnik: Tworzenie konspektu](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.

## <a name="enabling-support-for-outlining"></a>Włączanie obsługi konspektu
 `AutoOutlining`Wpis rejestru jest ustawiony na 1, aby włączyć automatyczne tworzenie konspektu. Automatyczne tworzenie konspektu ustawia analizę całego źródła, gdy plik zostanie załadowany lub zmieniony w celu zidentyfikowania ukrytych regionów i pokazania symboli konspektu. Konspekt można również kontrolować ręcznie przez użytkownika.

 Wartość `AutoOutlining` wpisu rejestru można uzyskać za pomocą <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> właściwości <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy. `AutoOutlining`Wpis rejestru można zainicjować przy użyciu nazwanego parametru do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybutu (zobacz [Rejestrowanie starszej wersji usługi językowej,](../../extensibility/internals/registering-a-legacy-language-service1.md) Aby uzyskać szczegółowe informacje).

## <a name="the-hidden-region"></a>Ukryty region
 Aby zapewnić tworzenie konspektów, usługa języka musi obsługiwać ukryte regiony. Są to zakresy tekstu, które mogą być rozwinięte lub zwinięte. Ukryte regiony mogą być rozdzielone symbolami języka standardowego, takimi jak nawiasy klamrowe, lub według symboli niestandardowych. Na przykład, C# ma `#region` / `#endregion` parę, która ogranicza ukryty region.

 Ukryte regiony są zarządzane przez Menedżera regionów ukrytych, który jest udostępniany jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> interfejs.

 Tworzenie konspektu używa ukrytych regionów <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> interfejs i zawiera zakres ukrytego regionu, bieżący widoczny stan oraz transparent, który ma być wyświetlany, gdy zasięg jest zwinięty.

 Analizator usługi językowej używa <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metody, aby dodać nowy ukryty region z zachowaniem domyślnym dla ukrytych regionów, podczas gdy <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> Metoda pozwala na dostosowanie wyglądu i zachowania konspektu. Po otrzymaniu ukrytych regionów do sesji ukrytego regionu program [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zarządza ukrytymi regionami dla usługi językowej.

 Jeśli konieczne jest określenie, kiedy sesja ukrytego regionu zostanie zniszczona, ukryty region jest zmieniany lub trzeba upewnić się, że określony ukryty region jest widoczny; należy utworzyć klasę z <xref:Microsoft.VisualStudio.Package.Source> klasy i zastąpić odpowiednie metody, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> , <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> , i <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A> , odpowiednio.

### <a name="example"></a>Przykład
 Poniżej przedstawiono uproszczony przykład tworzenia ukrytych regionów dla wszystkich par nawiasów klamrowych. Przyjęto założenie, że język zawiera dopasowanie nawiasów klamrowych i że nawiasy klamrowe mają być dopasowane, zawierają co najmniej nawiasy klamrowe ({i}). Takie podejście służy wyłącznie do celów informacyjnych. Pełna implementacja będzie miała pełną obsługę przypadków w programie <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> . Ten przykład pokazuje również, jak ustawić <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> preferencję na `true` czas tymczasowy. Alternatywą jest określenie `AutoOutlining` parametru nazwanego w `ProvideLanguageServiceAttribute` atrybucie pakietu językowego.

 W tym przykładzie założono reguły języka C# dla komentarzy, ciągów i literałów.

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
