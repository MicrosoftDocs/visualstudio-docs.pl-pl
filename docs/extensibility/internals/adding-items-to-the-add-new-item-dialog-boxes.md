---
title: Dodawanie elementów do okien dialogowych Dodawanie nowego elementu | Microsoft Docs
description: Dowiedz się, jak dodawać elementy do okna dialogowego Dodawanie nowego elementu w programie Visual Studio, aby można było wyświetlać szablony i elementy projektu do użycia w projektach.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 70bc1a0c4d90d8cab0b2193550773745fc2dd47e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904412"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Dodawanie elementów do okna dialogowego Dodawanie nowego elementu
Proces dodawania elementów do okna **dialogowego Dodawanie nowego elementu** rozpoczyna się od kluczy rejestru. Jak pokazano w poniższych wpisach rejestru, sekcja **AddItemTemplates** zawiera ścieżkę i nazwę  katalogu, w którym są umieszczane elementy udostępnione w oknie dialogowym Dodawanie nowego elementu.

> [!NOTE]
> Tabela bezpośrednio po segmencie kodu zawiera dodatkowe informacje o wpisie rejestru.

 Ta sekcja znajduje się w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects**.

 Pierwszy identyfikator GUID to identyfikator CLSID dla projektów tego typu. Drugi identyfikator GUID wskazuje zarejestrowany typ projektu dla szablonów Dodaj elementy:

 **\\{C061DB26-5833-11D2-96F5-00000000000} \\ AddItemTemplates \\ TemplatesDir \\ {ACEF4EB2-57CF-11D2-96F4-00000000000} \\ 1**

 **@** = #6

   =  \\ TemplatesDir &lt; Visual Studio instalacji zestawu SDK &gt; \\ VSIntegration \\ &lt; SomeFolder &gt; \\ &lt; SomePackage &gt; \\ &lt; &gt; \\ &lt; SomeProject SomeProjectItems&gt;

 **SortPriority** = dword:00000064

| Nazwa | Typ | Dane *(z pliku rgs)* | Opis |
|------------------|-----------| - | - |
| @ (wartość domyślna) | REG_SZ | #%IDS_ADDITEM_TEMPLATES_ENTRY% | Identyfikator zasobu dla **pozycji Dodaj szablony** elementów. |
| Val TemplatesDir | REG_SZ | %TEMPLATE_PATH% \\ &lt; SomeProjectItems&gt; | Ścieżka elementów projektu wyświetlanych w oknie dialogowym Kreatora **dodawania nowego** elementu. |
| Val SortPriority | REG_DWORD | 100 ( [!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)] ) | Określa kolejność sortowania w węźle drzewa plików wyświetlanych w **oknie dialogowym Dodawanie nowego** elementu. |

> [!NOTE]
> Identyfikatory GUID dla typów projektów Visual C# Visual Basic są następujące:
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}

 Katalog na liście **TemplatesDir,** którym jest *%TEMPLATE_PATH% \\ &lt; SomeProjectItems, &gt;* jest węzłem po lewej stronie drzewa okna dialogowego Dodawanie nowego elementu.  Dodatkowe elementy w drzewie są oparte na podkatalogu w tym katalogu głównym. Pliki dostępne do dodania do projektu to elementy w okienku po prawej stronie okna dialogowego Dodawanie **nowego** elementu.

 Zazwyczaj ten folder będzie zawierać pliki szablonów dla projektu, takie jak plik HTML szablonu lub *CPP,* oraz pliki *vsz* do uruchamiania kreatorów. Aby kontrolować sposób wyświetlania elementów, można również dołączyć *pliki vsdir* do lokalizacji nazw katalogów i ikon. Zlokalizowany ciąg to podpis wyświetlany w oknie dialogowym, który  reprezentuje ten węzeł w drzewie okna dialogowego Dodawanie nowego elementu.

 Nie trzeba jednak mieć wszystkiego w jednym pliku *vsdir.* Można mieć jeden *plik vsdir* dla każdego elementu w katalogu. Aby uzyskać więcej informacji, [zobacz plik kreatora (vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) i opis katalogu [szablonu (vsdir) plików](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

> [!NOTE]
> Pliki *.vsdir* w katalogach szablonów są opcjonalne. Jeśli chcesz tylko umieścić element projektu w katalogu i  wyświetlić go w oknie dialogowym Dodawanie nowego elementu, możesz umieścić ten plik w katalogu templates określonym w instrukcji **TemplatesDir.** Plik zostanie wyświetlony w okienku po  prawej stronie okna dialogowego Dodawanie nowego elementu dla tego projektu. Jeśli jednak chcesz wyświetlić zlokalizowany podpis do pliku lub ikony, musisz dołączyć co najmniej jeden plik *vsdir* do katalogu szablonów.

## <a name="group-project-items"></a>Grupowanie elementów projektu
 Jeśli chcesz, aby grupy szablonów  były zawarte w folderach w drzewie okna dialogowego Dodawanie nowego elementu, musisz mieć podkatalogi w katalogu głównym szablonu z elementami w nich zawartymi. Po **wyświetleniu okna dialogowego** Dodawanie nowego elementu użytkownicy zobaczą również podfoldery i będą mogli wybierać z nich elementy projektu.

 Priorytet sortowania w segmencie kodu określa, gdzie ten katalog szablonu zostanie utworzony w drzewie względem innych elementów węzła drzewa. W **oknie dialogowym** Dodawanie nowego elementu należy uwzględnić tylko priorytet sortowania, aby elementy były wyświetlane we właściwej lokalizacji w oknie dialogowym.

 Można również zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfejs do filtrowania elementów wyświetlanych w **oknie dialogowym** Dodawanie nowego elementu. Implementując ten interfejs, można skonfigurować jeden katalog szablonów na dysku, który zawiera na przykład 50 plików szablonów i kreatorów. W ten sposób można mieć różne typy projektów z 20 plikami, które należą do jednego typu projektu, pozostałe 30 plików należących do innego typu projektu oraz wszystkie pliki dostępne w projekcie typu ogólnego. W ten sposób, w zależności od tego, który szablon projektu został utworzony, można wyświetlić inny zestaw plików szablonu.

 Na przykład w projekcie Visual Basic można mieć projekty sieci Web i projekty klienckie. Formularze sieci Web nie są przydatnymi elementami do dodania do projektu klienta, a formularze systemu Windows nie są przydatnymi elementami do dodania do projektu serwera sieci Web. W związku z tym można utworzyć jeden katalog szablonów, który zawiera wszystkie pliki dla obu typów projektów. Następnie, implementując element , można ukryć elementy, które nie powinny być wyświetlane na podstawie typu projektu lub ustawień projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> w projekcie.

## <a name="filter-project-items"></a>Filtrowanie elementów projektu
 `IVsFilterAddProjectItemDlg2` Program umożliwia filtrowanie elementów w drzewie (okienko po lewej stronie) i plikach projektu (w okienku po prawej stronie) w następujący sposób:

- Według zlokalizowanych nazw (podpisów wyświetlanych w oknie dialogowym, które znajduje się w *pliku vsdir)* dostarczonych przez `IVsFilterAddProjectItemDlg` .

- Według rzeczywistych nazw plików i folderów na dysku (niez lokalnie — bez *pliku vsdir)* dostarczonych `IVsFilterAddProjectItemDlg` przez .

- Według kategorii dostarczonej przez `IVsFilterAddProjectItemDlg2` .

  Aby filtrować według kategorii, podaj ciąg kategorii do elementu w pliku *vsdir,* takiego jak formularz sieci *Web* lub *element* klienta w Visual Basic. Kod okna dialogowego pobiera klasyfikację kategorii z pliku *vsdir* i przekazuje ją do Ciebie. Następnie możesz przekazać te informacje do implementacji programu , aby filtrować okno dialogowe Dodawanie `IVsFilterAddProjectItemDlg2` nowego elementu według kategorii.  Można również filtrować elementy dla stron sieci Web lub jako przypadki aplikacji win32 klienta. Ponadto można identyfikować [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] otagowane elementy jako Microsoft Foundation Classes (MFC) lub elementy aktywnej biblioteki szablonów (ATL). Po zidentyfikowaniu tych elementów system projektu może zdefiniować własne klasyfikacje, aby można było filtrować system na podstawie kategorii i klasyfikacji.

  W przypadku zaimplementowania tej funkcji filtrowania nie trzeba mapować tabeli wszystkich elementów, które powinny być ukryte. Można po prostu klasyfikować elementy w typy i umieszczać klasyfikacje w pliku *vsdir* lub plikach. Następnie można ukryć wszystkie elementy, które mają określoną klasyfikację, implementując interfejs. W ten sposób można ustawić elementy  w oknie dialogowym Dodawanie nowego elementu jako dynamiczne na podstawie stanu w projekcie.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Identyfikatory CATID obiektów, które są zwykle używane do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [Dodawanie szablonów projektów i elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Plik opisu katalogu szablonu (vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [Plik kreatora (vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
