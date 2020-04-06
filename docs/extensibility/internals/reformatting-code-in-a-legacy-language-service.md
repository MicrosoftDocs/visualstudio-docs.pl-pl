---
title: Kod formatowania w starszej usłudze językowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd3e83c7299298b16a6fb3178b189479a80e1728
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705913"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Ponowne formatowanie kodu w starszej wersji usługi językowej

W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kodzie źródłowym można sformastrować przez normalizację użycia wcięć i odstępów. Może to obejmować wstawianie lub usuwanie spacji lub kart na początku każdego wiersza, dodawanie nowych linii między wierszami lub zastępowanie spacji kartami lub kartami spacjami.

> [!NOTE]
> Wstawianie lub usuwanie znaków nowego narzędzia może mieć wpływ na znaczniki, takie jak punkty przerwania i zakładki, ale dodawanie lub usuwanie spacji lub kart nie wpływa na znaczniki.

Użytkownicy mogą rozpocząć operację formatowania, wybierając **opcję Zaznaczanie formatu** lub **Formatuj dokument** z menu **Zaawansowane** w menu **Edycja.** Operację formatowania można również wyzwolić po wstawieniu fragmentu kodu lub określonego znaku. Na przykład po wpisaniu nawiasu zamykającego w języku C#wszystko między pasującym otwartym nawiasem klamrowym a nawiasem klamrowym zamykanego jest automatycznie wcięte do odpowiedniego poziomu.

Po [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wysłaniu **formatu zaznaczenia** lub **formatu dokumentu** <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> polecenia do <xref:Microsoft.VisualStudio.Package.Source> usługi języka, <xref:Microsoft.VisualStudio.Package.ViewFilter> klasa wywołuje metodę w klasie. Aby obsługiwać formatowanie, należy <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> zastąpić metodę i podać własny kod formatowania.

## <a name="enabling-support-for-reformatting"></a>Umożliwienie wsparcia dla reformowania

Aby `EnableFormatSelection` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> obsługiwać formatowanie, parametr musi `true` być ustawiony na podczas rejestracji VSPackage. Spowoduje to <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> ustawienie `true`właściwości na . Metoda <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> zwraca wartość tej właściwości. Jeśli zwraca true, <xref:Microsoft.VisualStudio.Package.ViewFilter> klasa <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>wywołuje .

## <a name="implementing-reformatting"></a>Wdrażanie reformowania

Aby zaimplementować sformarankowanie, należy wyprowadzić klasę z <xref:Microsoft.VisualStudio.Package.Source> klasy i zastąpić <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metodę. Obiekt <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> opisuje zakres do formatowania, a <xref:Microsoft.VisualStudio.Package.EditArray> obiekt przechowuje zmiany wprowadzone na rozpiętości. Należy zauważyć, że ten zakres może być cały dokument. Jednak ponieważ istnieje prawdopodobieństwo wielu zmian wprowadzonych do zakresu, wszystkie zmiany powinny być odwracalne w jednej akcji. Aby to zrobić, zawiń <xref:Microsoft.VisualStudio.Package.CompoundAction> wszystkie zmiany w obiekcie (zobacz sekcję "Korzystanie z klasy CompoundAction" w tym temacie).

### <a name="example"></a>Przykład

Poniższy przykład zapewnia, że po każdym przecinku w zaznaczeniu znajduje się pojedyncza spacja, chyba że po przecinku następuje karta lub znajduje się na końcu wiersza. Spływy po ostatnim przecinkach w wierszu są usuwane. Zobacz sekcję "Korzystanie z klasy CompoundAction" w tym temacie, <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> aby zobaczyć, jak ta metoda jest wywoływana z metody.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        private void DoFormatting(EditArray mgr, TextSpan span)
        {
            // Make sure there is one space after every comma unless followed
            // by a tab or comma is at end of line.
            IVsTextLines pBuffer = GetTextLines();
            if (pBuffer != null)
            {
                int    startIndex = span.iStartIndex;
                int    endIndex   = 0;
                string line       = "";
                // Loop over all lines in span
                for (int i = span.iStartLine; i <= span.iEndLine; i++)
                {
                    if (i < span.iEndLine)
                    {
                        pBuffer.GetLengthOfLine(i, out endIndex);
                    }
                    else
                    {
                        endIndex = span.iEndIndex;
                    }
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);

                    if (line.Length > 0)
                    {
                        int index = 0;
                        // Loop over all commas in line
                        while ((index = line.IndexOf(',', index)) != -1)
                        {
                            int spaceIndex = index + 1;
                            // Determine how many spaces after comma
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')
                            {
                                ++spaceIndex;
                            }

                            int      spaceCount      = spaceIndex - (index + 1);
                            string   replacementText = " ";
                            bool     fDoEdit         = true;
                            TextSpan editTextSpan    = new TextSpan();

                            editTextSpan.iStartLine  = i;
                            editTextSpan.iEndLine    = i;
                            editTextSpan.iStartIndex = index + 1;

                            if (spaceIndex == line.Length)
                            {
                                if (spaceCount > 0)
                                {
                                    // Delete spaces after a comma at end of line
                                    editTextSpan.iEndIndex = spaceIndex;
                                    replacementText = "";
                                }
                                else
                                {
                                    // Otherwise, do not add spaces if comma is
                                    // at end of line.
                                    fDoEdit = false;
                                }
                            }
                            else if (spaceCount == 0)
                            {
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')
                                {
                                    // Do not insert space if a tab follows
                                    // a comma.
                                    fDoEdit = false;
                                }
                                else
                                {
                                    // No space after comma so add a space.
                                    editTextSpan.iEndIndex = index + 1;
                                }
                            }
                            else if (spaceCount > 1)
                            {
                                // More than one space after comma, replace
                                // with a single space.
                                editTextSpan.iEndIndex = spaceIndex;
                            }
                            else
                            {
                                // Single space after a comma and not at end
                                // of the line, leave it alone.
                                fDoEdit = false;
                            }
                            if (fDoEdit)
                            {
                                // Add edit operation
                                mgr.Add(new EditSpan(editTextSpan, replacementText));
                            }
                            index = spaceIndex;
                        }
                    }
                    startIndex = 0; // All subsequent lines start at 0
                }
                // Apply all edits
                mgr.ApplyEdits();
            }
        }
    }
}
```

## <a name="using-the-compoundaction-class"></a>Korzystanie z CompoundAction Klasy

Wszystkie formatowanie wykonane na części kodu powinny być odwracalne w jednej akcji. Można to osiągnąć za <xref:Microsoft.VisualStudio.Package.CompoundAction> pomocą klasy. Ta klasa zawija zestaw operacji edycji w buforze tekstowym w jedną operację edycji.

### <a name="example"></a>Przykład

Oto przykład sposobu korzystania z <xref:Microsoft.VisualStudio.Package.CompoundAction> klasy. Zobacz przykład w sekcji "Implementowanie obsługi formatowania" w tym `DoFormatting` temacie na przykład metody.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override void ReformatSpan(EditArray mgr, TextSpan span)
        {
            string description = "Reformat code";
            CompoundAction ca = new CompoundAction(this, description);
            using (ca)
            {
                ca.FlushEditActions();      // Flush any pending edits
                DoFormatting(mgr, span);    // Format the span
            }
        }
    }
}
```

## <a name="see-also"></a>Zobacz też

- [Funkcje starszej wersji usługi językowej](legacy-language-service-features1.md)
