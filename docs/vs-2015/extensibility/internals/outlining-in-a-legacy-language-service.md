---
title: Zwijanie w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
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
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 356b3d49fa8eb74ef2352e6ba36597d1c39fecf4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751543"
---
# <a name="outlining-in-a-legacy-language-service"></a>Zwijanie w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Konspekt umożliwia zwijane złożony program Przegląd lub konspektu. Na przykład w języku C# może zostać zwinięty wszystkie metody w jeden wiersz, pokazujący tylko podpis metody. Ponadto aby pokazać tylko nazwy klasy i struktury może zostać zwinięty struktury i klasy. Wewnątrz pojedynczej metody złożonej logiki może zostać zwinięty będzie wyświetlana ogólny przepływ, takich jak wyświetlanie tylko pierwszy wiersz instrukcji `foreach`, `if`, i `while`.  
  
 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej, zobacz [wskazówki: Tworzenie konspektu](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.  
  
## <a name="enabling-support-for-outlining"></a>Włączanie obsługi konspekt  
 `AutoOutlining` Wpis rejestru jest ustawiona na 1, aby włączyć automatyczne tworzenie konspektu. Automatyczne tworzenie konspektu konfiguruje analizy całego źródła podczas ładowania lub zmienione w celu identyfikowania ukryte obszary i Pokaż symbole konspektu pliku. Tworzenie konspektu można także kontrolować ręcznie przez użytkownika.  
  
 Wartość `AutoOutlining` wpis rejestru można uzyskać za pośrednictwem <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> właściwość <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy. `AutoOutlining` Wpis rejestru mogą być zainicjowane z nazwany parametr do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybutu (patrz [rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md) Aby uzyskać szczegółowe informacje).  
  
## <a name="the-hidden-region"></a>Ukryty Region  
 Aby zapewnić Tworzenie konspektu, usługi w języka musi obsługiwać ukryte obszary. Oto zakresy tekst, który można rozwijać i zwijać. Ukryte obszary można ograniczać przez standardowe języka symbole, takie jak nawiasy klamrowe, lub niestandardowych symboli. Na przykład C# ma `#region` / `#endregion` pary ograniczającego ukryty region.  
  
 Ukryte regiony są zarządzane przez Menedżera ukryty region, który jest udostępniany jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> interfejsu.  
  
 Konspekt używa ukryte obszary <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> interfejs i zawierać zakres ukryty region, bieżący stan widoczne i Baner, który ma być wyświetlany, gdy zakres jest zwinięta.  
  
 Używa analizatora usługi w języka <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metody w celu dodania nowych ukryty region z domyślnym zachowaniem ukrytych regionów podczas <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metody umożliwia dostosowanie wyglądu i zachowania konspektu. Po ukryte obszary są podane z sesją ukryty region [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zarządza ukrytych regionów dla usługi w języka.  
  
 Jeśli zachodzi potrzeba określenia, kiedy niszczony jest sesja ukryty region, zmianie ukryta regionu lub musisz upewnić się, że określonego ukryty region jest widoczny; należy wyprowadzić klasę z <xref:Microsoft.VisualStudio.Package.Source> klasy i zastąpić właściwe metody <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, i <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, odpowiednio.  
  
### <a name="example"></a>Przykład  
 Oto uproszczony przykład tworzenia ukrytych regionów dla wszystkich par nawiasów klamrowych. Zakłada się, że język zapewnia parowanie nawiasów klamrowych i nawiasy klamrowe mają być dopasowywane zawiera co najmniej nawiasy klamrowe ({i}). To podejście jest tylko w celach ilustracyjnych. Pełną implementację miałby pełną obsługę przypadków w <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. W tym przykładzie przedstawiono również sposób ustawiania <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> preferencję `true` tymczasowo. Alternatywą jest określenie `AutoOutlining` o nazwie parametru w `ProvideLanguageServiceAttribute` atrybutu w pakiecie języka.  
  
 W tym przykładzie przyjęto założenie, C# zasady komentarze, ciągi znaków i literały.  
  
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
 [Funkcje usługi starszego języka](../../extensibility/internals/legacy-language-service-features1.md)   
 [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)

