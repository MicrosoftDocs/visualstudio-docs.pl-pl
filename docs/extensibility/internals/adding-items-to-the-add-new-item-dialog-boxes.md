---
title: Dodawanie elementów do Dodaj nowy element okna dialogowe | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d447090585a2314899bb2d6246c6fb450a9e767d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956052"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Dodawanie elementów do okna dialogowego Dodaj nowy element
Proces dodawania elementów do **Dodaj nowy element** okno dialogowe zaczyna się od kluczy rejestru. Jak pokazano w następujących wpisach rejestru **AddItemTemplates** sekcja zawiera ścieżkę i nazwę katalogu, w które elementy udostępnione w **Dodaj nowy element** są umieszczane okno dialogowe.  

> [!NOTE]
>  Tabela natychmiast po segment kodu zawiera dodatkowe informacje na temat wpisu rejestru.  

 W tej sekcji znajduje się w folderze **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects**.

 Pierwszy identyfikator GUID jest identyfikator CLSID dla projektów tego typu; drugi identyfikator GUID wskazuje typ projektu zarejestrowanego dla szablonów Dodaj elementy:  

 **\\{C061DB26-5833-11D2-96F5-000000000000} \\AddItemTemplates\\TemplatesDir\\{ACEF4EB2-57CF-11D2-96F4-000000000000}\\1**

 **@** = #6 

 **TemplatesDir** = \\&lt;ścieżka instalacji programu Visual Studio SDK&gt;\\VSIntegration\\&lt;SomeFolder&gt; \\ &lt;SomePackage&gt;\\&lt;SomeProject&gt;\\&lt;SomeProjectItems&gt;

 **SortPriority** = dword:00000064


| Nazwa | Typ | Dane (z *.rgs* pliku) | Opis |
|------------------|-----------| - | - |
| @ (Ustawienie domyślne) | REG_SZ | #% IDS_ADDITEM_TEMPLATES_ENTRY % | Identyfikator zasobu dla **elementu Dodawanie** szablonów. |
| Val TemplatesDir | REG_SZ | TEMPLATE_PATH %\\&lt;SomeProjectItems&gt; | Ścieżka wyświetlanych w oknie dialogowym dla elementów projektu **Dodaj nowy element** kreatora. |
| Val SortPriority | REG_DWORD | 100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]) | Określa porządek sortowania w węźle drzewa pliki wyświetlane w **Dodaj nowy element** okno dialogowe. |

> [!NOTE]
>  Identyfikatory GUID dla języka Visual C# i typów projektów języka Visual Basic są następujące: 
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  

 Katalog dla **TemplatesDir**, czyli *TEMPLATE_PATH %\\&lt;SomeProjectItems&gt;*, jest węzłem w lewej części **Dodaj Nowy element** drzewa okno dialogowe. Dodatkowe elementy w drzewie są oparte na podkatalogu w tym katalogu głównego. Pliki można dodać do projektu są elementy w prawym okienku **Dodaj nowy element** okno dialogowe.  

 Zazwyczaj ten folder będzie zawierać pliki szablonu projektu, taki jak kod HTML szablonu lub *.cpp* pliku i wszystkie *.vsz* pliki do uruchamiania kreatorów. Aby kontrolować sposób wyświetlania elementów, możesz również uwzględnić *.vsdir* pliki do lokalizowania nazwy katalogów i ikony. Zlokalizowany ciąg jest podpis, który pojawia się w oknie dialogowym, który reprezentuje ten węzeł w **Dodaj nowy element** drzewa okno dialogowe.  

 Jednakże, nie trzeba mieć wszystko w jednym *.vsdir* pliku. Może mieć jeden *.vsdir* pliku dla każdego elementu w katalogu. Aby uzyskać więcej informacji, zobacz [pliku kreatora (.vsz —)](../../extensibility/internals/wizard-dot-vsz-file.md) i [pliki (vsdir) opis katalogu szablonu](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  

> [!NOTE]
>  *.Vsdir* plików w katalogach szablonu są opcjonalne. Jeśli chcesz tylko umieścić element projektu w katalogu i wyświetl ją w **Dodaj nowy element** okno dialogowe, mogą umieścić ten plik w katalogu szablonów, określonym w **TemplatesDir** instrukcji. Plik zostanie wyświetlony w okienku po prawej stronie od **Dodaj nowy element** okno dialogowe dla tego projektu. Jednak jeśli chcesz wyświetlić podpis zlokalizowane dla pliku lub ikona, musisz dołączyć co najmniej jeden *.vsdir* pliku w katalogu szablonów.  

## <a name="group-project-items"></a>Grupowanie elementów projektu  
 Jeśli ma zawierać szablon grup w folderach w **Dodaj nowy element** drzewa okno dialogowe, konieczne jest posiadanie podkatalogów w katalogu głównym szablonu z elementami w nich. Gdy **Dodaj nowy element** użytkownikom zostanie wyświetlone okno dialogowe, będzie również obejrzeć podfoldery i mieć możliwość wyboru elementów projektu z nich.  

 Priorytet sortowania w segmencie kodu określa tworzona ten katalog szablonu w drzewie względem innych elementów w węźle drzewa. Aby uzyskać **Dodaj nowy element** okno dialogowe priorytet sortowania są wszystkie opcje, które należy uwzględnić, tak aby elementów, które będą wyświetlane w poprawnej lokalizacji, w oknie dialogowym.  

 Możesz również wdrożyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfejsu do filtrowania, co jest wyświetlane w **Dodaj nowy element** okno dialogowe. Implementując ten interfejs, możesz skonfigurować jeden szablon katalogu na dysku, który zawiera na przykład 50 plików szablonu i kreatora. W ten sposób może mieć różnych typach projektów z 20 plików, które należą do jednego projektu typu, 30 plików, które należą do innego typu projektu i wszystkie pliki należące do ogólnego typu projektu. W ten sposób, w zależności od tego, który projekt zostanie utworzony szablon, możesz wyświetlić inny zbiór plików szablonów.  

 Na przykład w projekcie języka Visual Basic, Niewykluczone, że projekty sieci Web i projektów klienckich. Formularze sieci Web nie są przydatne elementy do dodania do projektu klienta i formularze systemu windows nie są przydatne elementy do dodania do projektu serwera sieci Web. W związku z tym można utworzyć jeden katalog szablonu, który zawiera wszystkie pliki dla obu typów projektu. Następnie, implementując <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, można ukrywać elementy, które nie powinny być widoczne na podstawie typu projektu lub w ustawieniach projektu w projekcie.  

## <a name="filter-project-items"></a>Filtruj elementy projektu  
 `IVsFilterAddProjectItemDlg2` udostępnia filtrowania elementów drzewa (lewe okienko) i pliki projektu (w okienku po prawej stronie) w następujący sposób:  

- Przy użyciu zlokalizowanych nazw (podpisy wyświetlane w oknie dialogowym, który jest zawarty w *.vsdir* pliku) dostarczonych przez `IVsFilterAddProjectItemDlg`.  

- Według rzeczywistych nazw plików i folderów na dysku (niezlokalizowana — nie *.vsdir* pliku) dostarczonych przez `IVsFilterAddProjectItemDlg`.  

- Według kategorii, dostarczone przez `IVsFilterAddProjectItemDlg2`.  

  Aby filtrować według kategorii, podaj ciąg kategorii do elementu w *.vsdir* plików, takich jak *formularza sieci Web* lub *elementu klienta* w języku Visual Basic. Kodu pola dialogowego następnie pobiera Kategoria klasyfikacji z *.vsdir* plik i przekazuje je do Ciebie. Możesz następnie przekazać te informacje do implementacji `IVsFilterAddProjectItemDlg2` do filtrowania **Dodaj nowy element** okno dialogowe według kategorii. Można również filtrować elementy dla stron sieci Web lub jako przypadków aplikacji Win32 klienta. Ponadto możesz zidentyfikować [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] oznaczone elementy jako Microsoft Foundation Classes (MFC) lub aktywnego szablonu library (ATL) elementów. Po zidentyfikowaniu tych elementów, system projektu, można zdefiniować własne klasyfikacje, aby system można filtrować na podstawie kategorii i klasyfikacji.  

  W przypadku zaimplementowania tej funkcji filtru ma mapowania tabeli każdego elementu, który ma być ukryty. Możesz po prostu klasyfikowania elementów do typów i umieścić klasyfikacje *.vsdir* pliku lub plików. Następnie można ukryć elementy, które mają określoną klasyfikację, implementując interfejs. W ten sposób można zapewnić elementów w **Dodaj nowy element** dynamiczne okno dialogowe na podstawie stanu w projekcie.  

## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Identyfikatorów CatID obiektów, które zwykle służą do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Dodaj projekt oraz szablony elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Pliki (vsdir) opis katalogu szablonu](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Plik kreatora (vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)