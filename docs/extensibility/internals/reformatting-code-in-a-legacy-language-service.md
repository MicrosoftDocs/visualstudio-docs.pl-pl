---
title: Ponowne formatowanie kodu w starszej wersji usługi językowej | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae48e1b97b5c9194cf3081687ab31ea9f857e6c9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724757"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Ponowne formatowanie kodu w starszej wersji usługi językowej

W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kodzie źródłowym można ponownie sformatować przez znormalizowanie użycia wcięć i odstępów. Może to obejmować Wstawianie lub usuwanie spacji lub kart na początku każdego wiersza, dodawanie nowych wierszy między wierszami lub zastępowanie spacji znakami tabulacji lub tabulatorami spacjami.

> [!NOTE]
> Wstawianie lub usuwanie znaków nowego wiersza może mieć wpływ na znaczniki takie jak punkty przerwania i zakładki, ale Dodawanie lub usuwanie spacji lub kart nie ma wpływu na znaczniki.

Użytkownicy mogą rozpocząć operację ponownego formatowania, wybierając **opcję Formatuj zaznaczenie** lub **Formatuj dokument** z menu **Zaawansowane** w menu **Edycja** . Operację ponownego formatowania można również wyzwolić, gdy zostanie wstawiony fragment kodu lub określony znak. Na przykład po wpisaniu zamykającego nawiasu klamrowego C#, wszystkie elementy między odpowiednim otwierającym nawiasem klamrowym i zamykanym nawiasem klamrowym są automatycznie wcięte do odpowiedniego poziomu.

Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wysyła polecenie **formatowania lub** **Formatuj dokument** do usługi językowej, klasa <xref:Microsoft.VisualStudio.Package.ViewFilter> wywołuje metodę <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> w klasie <xref:Microsoft.VisualStudio.Package.Source>. Aby można było obsługiwać formatowanie, należy zastąpić metodę <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> i podać własny kod formatowania.

## <a name="enabling-support-for-reformatting"></a>Włączanie obsługi ponownego formatowania

Aby można było obsługiwać formatowanie, `EnableFormatSelection` parametr <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> musi być ustawiony na `true` po zarejestrowaniu pakietu VSPackage. Spowoduje to ustawienie właściwości <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> na `true`. Metoda <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> zwraca wartość tej właściwości. Jeśli zwraca wartość true, Klasa <xref:Microsoft.VisualStudio.Package.ViewFilter> wywołuje <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.

## <a name="implementing-reformatting"></a>Implementowanie ponownego formatowania

Aby zaimplementować ponowne formatowanie, należy utworzyć klasę z klasy <xref:Microsoft.VisualStudio.Package.Source> i zastąpić metodę <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>. Obiekt <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> opisuje zakres do formatowania, a obiekt <xref:Microsoft.VisualStudio.Package.EditArray> przechowuje zmiany wprowadzone w zakresie. Należy pamiętać, że ten zakres może być całym dokumentem. Jednak ze względu na to, że może być wiele zmian wprowadzonych w tym zakresie, wszystkie zmiany powinny być odwracalne w jednej akcji. W tym celu zawiń wszystkie zmiany w obiekcie <xref:Microsoft.VisualStudio.Package.CompoundAction> (zobacz sekcję "Używanie klasy CompoundAction" w tym temacie).

### <a name="example"></a>Przykład

Poniższy przykład gwarantuje, że istnieje pojedyncze miejsce po każdym przecinku w zaznaczeniu, chyba że przecinek następuje tabulator lub znajduje się na końcu wiersza. Spacje końcowe po ostatnim przecinku w wierszu są usuwane. Zobacz sekcję "Używanie klasy CompoundAction" w tym temacie, aby zobaczyć, jak ta metoda jest wywoływana z metody <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.

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

## <a name="using-the-compoundaction-class"></a>Korzystanie z klasy CompoundAction

Wszystkie ponowne formatowanie wykonywane w sekcji kodu powinno być odwracalne w jednej akcji. Można to zrobić za pomocą klasy <xref:Microsoft.VisualStudio.Package.CompoundAction>. Ta klasa otacza zestaw operacji edycji w buforze tekstowym w ramach jednej operacji edycji.

### <a name="example"></a>Przykład

Oto przykład użycia klasy <xref:Microsoft.VisualStudio.Package.CompoundAction>. Zapoznaj się z przykładem w sekcji "implementacja obsługi dla formatowania" w tym temacie, aby zapoznać się z przykładową metodą `DoFormatting`.

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

## <a name="see-also"></a>Zobacz także

- [Funkcje starszej wersji usługi językowej](legacy-language-service-features1.md)