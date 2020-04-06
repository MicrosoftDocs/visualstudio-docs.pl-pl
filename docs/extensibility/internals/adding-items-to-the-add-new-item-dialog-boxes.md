---
title: Dodawanie elementów do okien dialogowych Dodawanie nowego elementu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7f9e5c792785a23ad1674a50abeb4eb6d3cba9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710216"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Dodawanie elementów do okna dialogowego Dodawanie nowego elementu
Proces dodawania elementów do okna dialogowego **Dodawanie nowego elementu** rozpoczyna się od kluczy rejestru. Jak pokazano w następujących wpisach rejestru, **AddItemTemplates** sekcji zawiera ścieżkę i nazwę katalogu, w którym elementy udostępnione w oknie dialogowym **Dodawanie nowego elementu** są umieszczane.

> [!NOTE]
> Tabela bezpośrednio po segmencie kodu zawiera dodatkowe informacje o wpisie rejestru.

 Ta sekcja znajduje się w **obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects**.

 Pierwszy identyfikator GUID jest identyfikatorem CLSID dla projektów tego typu; drugi identyfikator GUID wskazuje zarejestrowany typ projektu szablonów Dodaj elementy:

 **\\{C061DB26-5833-11D2-96F5-0000000000} \\AddItemTemplates\\TemplatesDir\\{ACEF4EB2-57CF-11D2-96F4-00000000000}\\1**

 **@**= #6

 **TemplatesDir** = \\&lt;&gt;\\Visual Studio SDK ścieżka\\&lt;instalacji&gt;\\&lt;VSIntegration&gt;\\&lt;SomeFolder SomePackage SomeProject&gt;\\&lt;SomeProjectItems&gt;

 **SortPriority** = dword:00000064

| Nazwa | Typ | Dane (z pliku *rgs)* | Opis |
|------------------|-----------| - | - |
| @ (domyślnie) | REG_SZ | #%IDS_ADDITEM_TEMPLATES_ENTRY% | Identyfikator zasobu dla **szablonów dodaj elementy.** |
| Szablony ValDir | REG_SZ | %TEMPLATE_PATH%\\&lt;SomeProjectItems&gt; | Ścieżka elementów projektu wyświetlana w oknie dialogowym kreatora **Dodawanie nowego elementu.** |
| Wartość sortowania ValPriority | REG_DWORD | 100[!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]( ) | Określa kolejność sortowania w węźle drzewa plików wyświetlanych w oknie dialogowym **Dodawanie nowego elementu.** |

> [!NOTE]
> Identyfikatory GUIDS dla typów projektów Visual C# i Visual Basic są następujące:
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}

 Katalog wymieniony dla **TemplatesDir**, który jest *\\&lt;%TEMPLATE_PATH% SomeProjectItems&gt;*, jest węzłem po lewej stronie drzewa okna dialogowego Dodawanie nowego **elementu.** Dodatkowe elementy w drzewie są oparte na podkatalogu w tym katalogu głównym. Pliki dostępne do dodania do projektu to elementy w prawym okienku okna dialogowego **Dodawanie nowego elementu.**

 Zazwyczaj ten folder będzie zawierał pliki szablonów dla projektu, takie jak szablon HTML lub *.cpp,* oraz wszystkie pliki *vsz* do uruchamiania kreatorów. Aby kontrolować sposób wyświetlania elementów, można również dołączyć pliki *vsdir* do lokalizowania nazw katalogów i ikon. Zlokalizowany ciąg to podpis wyświetlany w oknie dialogowym reprezentującym ten węzeł w drzewie okna dialogowego **Dodawanie nowego elementu.**

 Nie musisz jednak mieć wszystkiego w jednym pliku *vsdir.* Dla każdego elementu w katalogu może być 1 plik *vsdir.* Aby uzyskać więcej informacji, zobacz [Pliki pliku Kreatora (vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) i [Opis katalogu szablonu (vsdir) pliki](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

> [!NOTE]
> Pliki *vsdir* w katalogach szablonów są opcjonalne. Jeśli chcesz tylko umieścić element projektu w katalogu i wyświetlić go w oknie dialogowym **Dodawanie nowego elementu,** możesz umieścić ten plik w katalogu szablonów określonym w instrukcji **TemplatesDir.** Plik zostanie wyświetlony w prawym okienku okna dialogowego **Dodawanie nowego elementu** dla tego projektu. Jeśli jednak chcesz wyświetlić zlokalizowany podpis dla pliku lub ikony, musisz dołączyć co najmniej jeden plik *vsdir* w katalogu szablonów.

## <a name="group-project-items"></a>Grupowanie elementów projektu
 Jeśli chcesz zawierać grupy szablonów w folderach w drzewie okna dialogowego **Dodawanie nowego elementu,** musisz mieć podkatalogi w katalogu szablonów głównych z elementami w nich zawartymi. Gdy okno dialogowe **Dodawanie nowego elementu** jest wyświetlane użytkownikom, zobaczą również podfoldery i będą mogli wybrać z nich elementy projektu.

 Priorytet sortowania w segmencie kodu określa, gdzie ten katalog szablonu zostanie utworzony w drzewie względem innych elementów węzła drzewa. W przypadku okna dialogowego **Dodawanie nowego elementu** priorytet sortowania to wszystko, co należy uwzględnić, aby elementy były wyświetlane we właściwej lokalizacji w oknie dialogowym.

 Można również zaimplementować interfejs, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> aby filtrować to, co jest wyświetlane w oknie dialogowym Dodawanie nowego **elementu.** Implementując ten interfejs, można skonfigurować jeden katalog szablonów na dysku, który zawiera na przykład 50 plików szablonów i kreatorów. W ten sposób można mieć różne typy projektów z 20 plików, które należą do jednego typu projektu, inne 30 plików, które należą do innego typu projektu i wszystkie pliki dostępne w ogólnym typie projektu. W ten sposób, w zależności od tego, który szablon projektu jest tworzony, można wyświetlić inny zestaw plików szablonów.

 Na przykład w projekcie języka Visual Basic mogą być projekty sieci Web i projekty klientów. Formularze sieci Web nie są przydatnymi elementami do dodania do projektu klienckiego, a formularze systemu Windows nie są przydatnymi elementami do dodania do projektu serwera sieci Web. W związku z tym można utworzyć jeden katalog szablonów, który zawiera wszystkie pliki dla obu typów projektu. Następnie implementując <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>program , można ukryć elementy, które nie powinny być wyświetlane na podstawie typu ustawień projektu lub projektu w projekcie.

## <a name="filter-project-items"></a>Filtrowanie elementów projektu
 `IVsFilterAddProjectItemDlg2`umożliwia filtrowanie elementów w drzewie (lewe okienko) i plików projektu (prawe okienko) w następujący sposób:

- Przez zlokalizowane nazwy (podpisy wyświetlane w oknie dialogowym, które znajduje się `IVsFilterAddProjectItemDlg`w pliku *vsdir)* dostarczone przez program .

- Według rzeczywistych nazw plików i folderów na dysku (niezlokalizowanych — `IVsFilterAddProjectItemDlg`bez pliku *vsdir)* dostarczonych przez program .

- Według kategorii, dostarczone `IVsFilterAddProjectItemDlg2`przez .

  Aby filtrować według kategorii, podaj ciąg kategorii do elementu w pliku *vsdir,* takiego jak *formularz sieci Web* lub element *klienta* w języku Visual Basic. Kod okna dialogowego pobiera klasyfikację kategorii z pliku *vsdir* i przekazuje ją do Ciebie. Następnie można przekazać te informacje `IVsFilterAddProjectItemDlg2` do implementacji, aby filtrować okno dialogowe **Dodawanie nowego elementu** według kategorii. Można również filtrować elementy dla stron sieci Web lub jako przypadki aplikacji klienta Win32. Ponadto można zidentyfikować [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] oznakowane elementy jako elementy klasy Microsoft Foundation (MFC) lub aktywne elementy biblioteki szablonów (ATL). Podczas identyfikowania tych elementów system projektu może definiować własne klasyfikacje, dzięki czemu system może być filtrowany na podstawie kategorii i klasyfikacji.

  Jeśli zaimplementujesz tę funkcję filtru, nie trzeba mapować tabeli każdego elementu, który powinien być ukryty. Można po prostu sklasyfikować elementy do typów i umieścić klasyfikacje w pliku *vsdir* lub plikach. Następnie można ukryć dowolny z elementów, które mają określonej klasyfikacji, implementując interfejs. W ten sposób można dynamicznie elementów w oknie dialogowym **Dodawanie nowego elementu** na podstawie stanu w projekcie.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Rejestrowanie szablonów projektów i towarów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Catidy dla obiektów, które są zwykle używane do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [Dodawanie szablonów elementów projektu i projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Pliki opisu katalogu szablonu (.vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [Plik Kreatora (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
