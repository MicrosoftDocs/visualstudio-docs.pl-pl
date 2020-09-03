---
title: Projektowanie tabeli poleceń XML (. Vsct) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708752"
---
# <a name="design-xml-command-table-vsct-files"></a>Projektowanie plików tabeli poleceń XML (. vsct)
Plik tabeli poleceń XML (*. vsct*) opisuje układ i wygląd elementów poleceń dla pakietu VSPackage. Elementy poleceń obejmują przyciski, pola kombi, menu, paski narzędzi i grupy elementów poleceń. W tym artykule opisano pliki tabeli poleceń XML, ich wpływ na elementy poleceń i menu oraz sposób ich tworzenia.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Polecenia, menu, grupy i plik. vsct
 Pliki *. vsct* są zorganizowane wokół poleceń, menu i grup poleceń. Tagi XML w pliku *. vsct* reprezentują każdy z tych elementów, wraz z innymi elementami skojarzonymi, takimi jak przyciski poleceń, umieszczanie poleceń i mapy bitowe.

 Po utworzeniu nowego pakietu VSPackage przez uruchomienie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] szablonu pakietu, szablon generuje plik *. vsct* z niezbędnymi elementami dla polecenia menu, okna narzędzi lub edytorem niestandardowym, w zależności od wybranych opcji. Plik *. vsct* można następnie zmodyfikować w taki sposób, aby spełniał wymagania określonego pakietu VSPackage. Przykłady sposobu modyfikowania pliku *vsct* można znaleźć w temacie [rozszerzając menu i polecenia](../../extensibility/extending-menus-and-commands.md).

 Aby utworzyć nowy, pusty plik *. vsct* , zobacz [How to: Create a *. vsct* plik](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Po utworzeniu należy dodać do pliku elementy XML, atrybuty i wartości, aby opisać układ elementu polecenia. Aby uzyskać szczegółowy schemat XML, zobacz [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Różnice między plikami. ctc i. vsct
 Chociaż znaczenie za tagami XML w pliku *. vsct* są takie same jak Tagi w obecnie przestarzały format pliku *CTC.* ich implementacja jest nieco różna:

- Nowy **\<extern>** tag to miejsce, w którym odwołujesz się do innych plików *h* , które mają być skompilowane, takich jak pliki na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pasku narzędzi.

- Chociaż pliki *. vsct* obsługują instrukcję **/include** , podobnie jak pliki *CTC* , funkcja zawiera również nowy **\<import>** element. Różnica polega na tym, że **/include** zawiera *wszystkie* informacje, a **\<import>** tylko nazwy.

- Pliki *. CTC* wymagają pliku nagłówkowego, w którym definiujesz dyrektywy preprocesora, jeden nie jest wymagany dla plików *. vsct* . Zamiast tego należy umieścić dyrektywy w tabeli symboli znajdujące się w **\<Symbol>** elementach znajdujących się w dolnej części pliku *. vsct* .

- pliki *. vsct* oferują **\<Annotation>** tag, który umożliwia osadzanie dowolnych informacji, takich jak notatki lub obrazy.

- Wartości są przechowywane jako atrybuty w elemencie.

- Flagi poleceń można przechowywać pojedynczo lub na stosie.  Funkcja IntelliSense nie działa jednak w przypadku stosowych flag poleceń. Aby uzyskać więcej informacji na temat flag poleceń, zobacz [element CommandFlag](../../extensibility/command-flag-element.md).

- Można określić wiele typów, takich jak zwijanie list rozwijanych, kombi itd.

- Identyfikatory GUID nie są weryfikowane.

- Każdy element interfejsu użytkownika ma ciąg, który reprezentuje wyświetlany tekst.

- Element nadrzędny jest opcjonalny. W przypadku pominięcia zostanie użyta *Grupa wartości nieznana* .

- Argument *ikony* jest opcjonalny.

- Sekcja mapy bitowej: Ta sekcja jest taka sama jak w pliku *. CTC* , z tą różnicą, że można teraz określić nazwę pliku za pośrednictwem href, który zostanie pobrany przez kompilator *vsct.exe* w czasie kompilacji.

- ResID: można użyć starego identyfikatora zasobu mapy bitowej i nadal działa tak samo jak w plikach *. CTC* .

- HRef: Nowa metoda, która umożliwia określenie nazwy pliku dla zasobu mapy bitowej. Przyjęto założenie, że wszystkie są używane, aby można było pominąć użytą sekcję. Kompilator najpierw szuka zasobów lokalnych dla pliku, a następnie w dowolnych udziałach sieciowych i wszystkich zasobach zdefiniowanych przez przełącznik **/i** .

- Powiązanie klawiszy: nie trzeba już określać emulatora. Jeśli określisz, kompilator przyjmie, że edytor i emulator są takie same.

- Keychord: Keychord został porzucony. Nowy format to *Klucz1, MOD1, klucz2, Mod2*.  Można określić znak, szesnastkowy lub VK.

Nowy kompilator *vsct.exe*, kompiluje pliki *. CTC* i *. vsct* . Jednak stary kompilator *ctc.exe* nie rozpoznaje ani nie kompiluje plików *vsct* .

Możesz użyć kompilatora *vsct.exe* , aby skonwertować istniejący plik *. Dyrektor ds* do pliku *. vsct* . Aby uzyskać więcej informacji, zobacz [How to: Create a. vsct plik z istniejącego pliku. Dyrektor ds](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>Vsct — elementy pliku
 Tabela poleceń ma następującą hierarchię i elementy:

- [Element](../../extensibility/commandtable-element.md): reprezentuje wszystkie polecenia, grupy menu i menu skojarzone z pakietu VSPackage.

- [Element extern](../../extensibility/extern-element.md): odwołuje się do wszystkich zewnętrznych plików. h, które chcesz scalić z plikiem *. vsct* .

- [Include — element](../../extensibility/include-element.md): odwołuje się do wszelkich dodatkowych plików nagłówkowych (. h), które chcesz skompilować wraz z plikiem *. vsct* . Plik *. vsct* może zawierać pliki *. h* zawierające stałe, które definiują polecenia, grupy menu i menu zapewniane przez środowisko IDE lub inne pakietu VSPackage.

- [Polecenie Commands](../../extensibility/commands-element.md): reprezentuje wszystkie poszczególne polecenia, które mogą być wykonywane. Każde polecenie ma cztery następujące elementy podrzędne:

- [Element menu](../../extensibility/menus-element.md): reprezentuje wszystkie menu i paski narzędzi w pakietu VSPackage. Menu są kontenerami dla grup poleceń.

- [Element Groups](../../extensibility/groups-element.md): reprezentuje wszystkie grupy w pakietu VSPackage. Grupy są kolekcjami poszczególnych poleceń.

- [Element Buttons](../../extensibility/buttons-element.md): reprezentuje wszystkie przyciski poleceń i elementy menu w pakietu VSPackage. Przyciski są kontrolkami wizualnymi, które mogą być skojarzone z poleceniami.

- [Bitmapy, element](../../extensibility/bitmaps-element.md): reprezentuje wszystkie mapy bitowe dla wszystkich przycisków w pakietu VSPackage. Mapy bitowe są obrazami wyświetlanymi obok lub na przyciskach poleceń, w zależności od kontekstu.

- [Element CommandPlacements](../../extensibility/commandplacements-element.md): wskazuje dodatkowe lokalizacje, w których poszczególne polecenia powinny znajdować się w menu pakietu VSPackage.

- [VisibilityConstraints Element](../../extensibility/visibilityconstraints-element.md): określa, czy polecenie ma być wyświetlane przez cały czas, czy też tylko w określonych kontekstach, na przykład gdy wyświetlane jest konkretne okno dialogowe lub okno. Menu i polecenia, które mają wartość dla tego elementu, będą wyświetlane tylko wtedy, gdy określony kontekst jest aktywny. Domyślnym zachowaniem jest wyświetlanie polecenia przez cały czas.

- [Element powiązań](../../extensibility/keybindings-element.md)klawiszy: określa dowolne powiązania klucza dla poleceń. Oznacza to, że jedna lub więcej kombinacji klawiszy, które muszą zostać naciśnięte, aby wykonać polecenie, takie jak **Ctrl** + **S**.

- [UsedCommands](../../extensibility/usedcommands-element.md): informuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowisko, że mimo że określone polecenie jest zaimplementowane przez inny kod, gdy bieżący pakietu VSPackage jest aktywny, udostępnia implementację poleceń.

- [Element symboli](../../extensibility/symbols-element.md): zawiera nazwy symboli i identyfikatory GUID dla wszystkich poleceń w pakiecie.

## <a name="vsct-file-design-guidelines"></a>wytyczne dotyczące projektowania plików. vsct
 Aby pomyślnie zaprojektować plik *. vsct* , postępuj zgodnie z poniższymi wskazówkami.

- Polecenia można umieścić tylko w grupach, grupy można umieścić tylko w menu, a menu można umieścić tylko w grupach. W środowisku IDE są wyświetlane tylko menu, a nie są to grupy i polecenia.

- Podmenu nie można bezpośrednio przypisywać do menu, ale muszą być przypisane do grupy, która jest z kolei przypisana do menu.

- Polecenia, podmenu i grupy można przypisywać do jednej grupy nadrzędnej lub menu przy użyciu pola nadrzędnego definicji dyrektywy.

- Organizowanie tabeli poleceń wyłącznie za pomocą pól nadrzędnych w dyrektywach ma znaczny limit. Dyrektywy definiujące obiekty mogą przyjmować tylko jeden argument nadrzędny.

- Ponowne użycie poleceń, grup lub podmenu wymaga zastosowania nowej dyrektywy do utworzenia nowego wystąpienia obiektu z własną `GUID:ID` parą.

- Każda `GUID:ID` para musi być unikatowa. Użycie polecenia, które ma na przykład zostać umieszczone w menu, na pasku narzędzi lub w menu kontekstowym, jest obsługiwane przez <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs.

- Polecenia i podmenu można także przypisać do wielu grup, a grupy można przypisywać do wielu menu za pomocą [elementu Commands](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>Informacje o pliku. vsct
 Jeśli wprowadzisz zmiany w pliku *. vsct* po obu tych kompilacjach i umieścisz je w natywnej satelitarnej bibliotece DLL, należy uruchomić **devenv.exe/Setup/nosetupvstemplates**. Spowoduje to wymuszenie ponownego odczytania zasobów pakietu VSPackage określonych w rejestrze eksperymentalnym oraz wewnętrznej bazy danych, która [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ma zostać przetworzona.

 Podczas opracowywania można tworzyć i rejestrować wiele projektów pakietu VSPackage w przypadku eksperymentalnych gałęzi rejestru, które mogą prowadzić do mylącego bałaganu w środowisku IDE. Aby rozwiązać ten problem, można zresetować program eksperymentalny do ustawień domyślnych, aby usunąć wszystkie zarejestrowane pakietów VSPackage i wszelkie zmiany, które mogły zostać wprowadzone do IDE. Aby zresetować pakiet eksperymentalny, użyj narzędzia CreateExpInstance.exe dołączonego do zestawu Visual Studio SDK. Można go znaleźć pod adresem:

 *% PROGRAMFILES (x86)% \ Visual Studio \\ \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 Uruchom narzędzie za pomocą polecenia **CreateExpInstance/Reset**. Należy pamiętać, że to narzędzie usuwa z eksperymentalnego programu Hive wszystkie zarejestrowane pakietów VSPackage nie są zwykle instalowane z programem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Zobacz też
- [Poszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md)
