---
title: Projektowanie tabeli poleceń XML (. Vsct) Pliki | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcd29aee98139bb151c87590b256df6b8370abff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708752"
---
# <a name="design-xml-command-table-vsct-files"></a>Projektowanie plików tabeli poleceń XML (vsct)
Plik tabeli poleceń XML (*vsct*) opisuje układ i wygląd elementów poleceń dla programu VSPackage. Elementy poleceń obejmują przyciski, pola kombi, menu, paski narzędzi i grupy elementów poleceń. W tym artykule opisano pliki tabel poleceń XML, ich wpływ na elementy poleceń i menu oraz sposób ich tworzenia.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Polecenia, menu, grupy i plik .vsct
 Pliki *vsct* są uporządkowane wokół poleceń, menu i grup poleceń. Znaczniki XML w pliku *vsct* reprezentują każdy z tych elementów, wraz z innymi powiązanymi elementami, takimi jak przyciski poleceń, rozmieszczenie poleceń i mapy bitowe.

 Podczas tworzenia nowego vsPackage przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uruchomienie szablonu pakietu, szablon generuje plik *.vsct* z elementów niezbędnych do polecenia menu, okna narzędzia lub edytora niestandardowego, w zależności od wybranych. Ten plik *vsct* można następnie zmodyfikować, aby spełnić wymagania określonego vsPackage. Aby zapoznać się z przykładami modyfikowania pliku *vsct,* zobacz [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).

 Aby utworzyć nowy, pusty plik *vsct,* zobacz [Jak: Tworzenie pliku *vsct* ](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Po utworzeniu do pliku można dodać elementy XML, atrybuty i wartości, aby opisać układ elementu polecenia. Aby uzyskać szczegółowy schemat XML, zobacz [odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Różnice między plikami ctc i .vsct
 Podczas gdy znaczenie znaczników XML w pliku *vsct* jest takie samo jak te znaczniki w obecnie przestarzałym formacie pliku *.ctc,* ich implementacja jest nieco inna:

- Nowy ** \<>** tag jest, gdzie odwołujesz się do innych plików *.h* do skompilowania, takich jak te pliki dla paska [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] narzędzi.

- Podczas gdy pliki *.vsct* obsługują instrukcję **/include,** tak jak pliki *ctc,* zawiera również nowy ** \<element importu>.** Różnica polega **na tym, że /include** przynosi *wszystkie* informacje, podczas gdy ** \<import>** przynosi tylko nazwy.

- Podczas gdy pliki *ctc* wymagają pliku nagłówka, w którym definiujesz dyrektywy preprocesora, nie jest wymagany dla plików *vsct.* Zamiast tego umieść dyrektywy w tabeli symboli, znajdującej ** \<** się w elementach Symbol>, znajdującej się w dolnej części pliku *vsct.*

- *Pliki vsct* zawierają ** \<adnotację>** tag, który umożliwia osadzenie dowolnych informacji, takich jak notatki, a nawet obrazy.

- Wartości są przechowywane jako atrybuty elementu.

- Flagi poleceń mogą być przechowywane indywidualnie lub ułożone.  IntelliSense nie działa jednak na skumulowanych flagach poleceń. Aby uzyskać więcej informacji na temat flag poleceń, zobacz [CommandFlag element](../../extensibility/command-flag-element.md).

- Można określić wiele typów, takich jak listy rozwijane podziału, kombinacje itp.

- Identyfikatory GUID nie są sprawdzane.

- Każdy element interfejsu użytkownika ma ciąg, który reprezentuje tekst, który jest wyświetlany wraz z nim.

- Element nadrzędny jest opcjonalny. Jeśli pominięto, używana jest wartość *Grupa Nieznany.*

- *Icon* Argument jest opcjonalny.

- Sekcja Bitmapa: Ta sekcja jest taka sama jak w pliku *ctc,* z tą różnicą, że można teraz określić nazwę pliku za pośrednictwem href, który zostanie pobrany przez kompilator *vsct.exe* w czasie kompilacji.

- ResID: Stary identyfikator zasobu mapy bitowej może być używany i nadal działa tak samo jak w plikach *ctc.*

- HRef: Nowa metoda, która pozwala określić nazwę pliku dla zasobu mapy bitowej. Zakłada się, że wszystkie są używane, więc można pominąć używane sekcji. Kompilator najpierw wyszuka zasoby lokalne dla pliku, a następnie na wszystkich udziałach netto i wszystkie zasoby zdefiniowane przez przełącznik **/I.**

- Keybinding: Nie trzeba już określać emulatora. Jeśli określisz jeden, kompilator przyjmie, że edytor i emulator są takie same.

- Klucz: Kluczord został usunięty. Ten nowy układ graficzny jest *Key1,Mod1,Key2,Mod2.*  Można określić znak, szesnastkową lub stałą VK.

Nowy kompilator *vsct.exe*kompiluje zarówno pliki *ctc,* jak i *vsct.* Stary kompilator *ctc.exe* nie rozpozna ani nie skompiluje plików *.vsct.*

Kompilator *vsct.exe* służy do konwertowania istniejącego pliku *cto* na plik *vsct.* Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie pliku vsct z istniejącego pliku cto](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>Elementy pliku vsct
 Tabela poleceń ma następującą hierarchię i elementy:

- [CommandTable element:](../../extensibility/commandtable-element.md)Reprezentuje wszystkie polecenia, grupy menu i menu skojarzone z VSPackage.

- [Element Extern](../../extensibility/extern-element.md): Odwołuje się do wszelkich zewnętrznych plików .h, które chcesz scalić z plikiem *vsct.*

- [Dołącz element](../../extensibility/include-element.md): Odwołuje się do wszelkich dodatkowych plików nagłówka (.h), które chcesz skompilować wraz z plikiem *vsct.* Plik *.vsct* może zawierać pliki *.h* zawierające stałe definiujące polecenia, grupy menu i menu, które zapewnia IDE lub inny VSPackage.

- [Element Polecenia](../../extensibility/commands-element.md): Reprezentuje wszystkie poszczególne polecenia, które mogą być wykonywane. Każde polecenie ma następujące cztery elementy podrzędne:

- [Menu element:](../../extensibility/menus-element.md)Reprezentuje wszystkie menu i paski narzędzi w VSPackage. Menu są kontenerami dla grup poleceń.

- [Elementy grupy:](../../extensibility/groups-element.md)Reprezentuje wszystkie grupy w VSPackage. Grupy są kolekcjami poszczególnych poleceń.

- [Element Przyciski:](../../extensibility/buttons-element.md)Reprezentuje wszystkie przyciski poleceń i elementy menu w vspackage. Przyciski są wizualne formanty, które mogą być skojarzone z poleceniami.

- [Bitmaps element:](../../extensibility/bitmaps-element.md)Reprezentuje wszystkie mapy bitowe dla wszystkich przycisków w VSPackage. Mapy bitowe to obrazy wyświetlane obok przycisków poleceń lub na ich podstawie, w zależności od kontekstu.

- [CommandPlacements element:](../../extensibility/commandplacements-element.md)Wskazuje dodatkowe lokalizacje, w których poszczególne polecenia powinny być umiejscowione w menu vsPackage.

- [WidocznośćWłaściwość element:](../../extensibility/visibilityconstraints-element.md)Określa, czy polecenie jest wyświetlane przez cały czas, czy tylko w określonych kontekstach, takich jak wyświetlanie określonego okna dialogowego lub okna. Menu i polecenia, które mają wartość dla tego elementu będą wyświetlane tylko wtedy, gdy określony kontekst jest aktywny. Domyślnym zachowaniem jest wyświetlanie polecenia przez cały czas.

- [KeyBindings element:](../../extensibility/keybindings-element.md)Określa wszelkie powiązania klucza dla poleceń. Oznacza to, że co najmniej jedna kombinacja klawiszy, które muszą zostać wciśnięte w celu wykonania polecenia, na przykład **Ctrl**+**S**.

- [UsedCommands element:](../../extensibility/usedcommands-element.md)Informuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowisko, że chociaż określone polecenie jest implementowane przez inny kod, gdy bieżący VSPackage jest aktywny, zapewnia implementację polecenia.

- [Symbole:](../../extensibility/symbols-element.md)Zawiera nazwy symboli i identyfikatory GUID dla wszystkich poleceń w pakiecie.

## <a name="vsct-file-design-guidelines"></a>Wskazówki dotyczące projektowania plików vsct
 Aby pomyślnie zaprojektować plik *vsct,* postępuj zgodnie z tymi wytycznymi.

- Polecenia można umieszczać tylko w grupach, grupy mogą być umieszczane tylko w menu, a menu można umieszczać tylko w grupach. Tylko menu są faktycznie wyświetlane w IDE, grupy i polecenia nie są.

- Podmenu nie można bezpośrednio przypisać do menu, ale musi być przypisany do grupy, która z kolei jest przypisana do menu.

- Polecenia, podmenu i grupy można przypisać do jednej grupy nadrzędnej lub menu przy użyciu pola nadrzędnego ich definiowania dyrektywy.

- Organizowanie tabeli poleceń wyłącznie za pośrednictwem pól nadrzędnych w dyrektywach ma istotne ograniczenie. Dyrektywy, które definiują obiekty może mieć tylko jeden argument nadrzędny.

- Ponowne użycie poleceń, grup lub podmenu wymaga użycia nowej dyrektywy w celu utworzenia `GUID:ID` nowego wystąpienia obiektu z własną parą.

- Każda `GUID:ID` para musi być unikatowa. Ponowne pożyczenie polecenia, które zostało na przykład umieszczone w menu, pasku narzędzi lub w <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> menu kontekstowym, jest obsługiwane przez interfejs.

- Polecenia i podmenu można również przypisać do wielu grup, a grupy można przypisać do wielu menu za pomocą [elementu Polecenia](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>notatki z plików vsct
 Jeśli po skompilowaniu pliku vsct zostaną wprowadzone jakiekolwiek zmiany w pliku *vsct* i umieścisz go w natywnej satelicie DLL, należy uruchomić **devenv.exe /setup /nosetupvstemplates**. W ten sposób wymusza vspackage zasobów określonych w rejestrze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eksperymentalnym do ponownego przeczytania i wewnętrznej bazy danych, która opisuje, aby zostać przebudowany.

 Podczas tworzenia jest możliwe dla wielu projektów VSPackage do utworzenia i zarejestrowane w gałęzi rejestru eksperymentalnego, które mogą prowadzić do mylące bałaganu w IDE. Aby rozwiązać ten problem, można zresetować gałęzi eksperymentalnej do ustawień domyślnych, aby usunąć wszystkie zarejestrowane vspackages i wszelkie zmiany, które mogą mieć wprowadzone do IDE. Aby zresetować gałęzi eksperymentalnej, należy użyć CreateExpInstance.exe narzędzie, który jest dostarczany z zestawu SDK programu Visual Studio. Można go znaleźć na:

 *%PROGRAMFILES(x86)%\Wersja\\\<programu Visual Studio> zestaw SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 Uruchom narzędzie za pomocą polecenia **CreateExpInstance /Reset**. Należy pamiętać, że to narzędzie usuwa z gałęzi eksperymentalnej wszystkie zarejestrowane VSPackages nie normalnie zainstalowany z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md)
