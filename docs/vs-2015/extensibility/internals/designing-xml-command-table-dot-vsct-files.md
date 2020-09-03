---
title: Projektowanie tabeli poleceń XML (. Vsct) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 987536af051de4a66b3eccadb105fd98455ddf06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196848"
---
# <a name="designing-xml-command-table-vsct-files"></a>Projektowanie tabeli poleceń XML (pliki Vsct)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Plik tabeli poleceń XML (. vsct) opisuje układ i wygląd elementów poleceń dla pakietu VSPackage. Elementy poleceń obejmują przyciski, pola kombi, menu, paski narzędzi i grupy elementów poleceń. W tym temacie opisano pliki tabeli poleceń XML, ich wpływ na elementy poleceń i menu oraz sposób ich tworzenia.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>Polecenia, menu, grupy i plik. vsct  
 pliki. vsct są zorganizowane wokół poleceń, menu i grup poleceń. Tagi XML w pliku. vsct reprezentują każdy z tych elementów, wraz z innymi elementami skojarzonymi, takimi jak przyciski poleceń, umieszczanie poleceń i mapy bitowe.  
  
 Po utworzeniu nowego pakietu VSPackage przez uruchomienie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] szablonu pakietu, szablon generuje plik. vsct z niezbędnymi elementami dla polecenia menu, okna narzędzi lub edytorem niestandardowym, w zależności od wybranych opcji. Plik. vsct można następnie zmodyfikować w taki sposób, aby spełniał wymagania określonego pakietu VSPackage. Przykłady sposobu modyfikowania pliku. vsct można znaleźć w przykładach [rozszerzających menu i polecenia](../../extensibility/extending-menus-and-commands.md).  
  
 Aby utworzyć nowy, pusty plik. vsct, zobacz [How to: Create a. Plik vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Po utworzeniu należy dodać do pliku elementy XML, atrybuty i wartości, aby opisać układ elementu polecenia. Aby uzyskać szczegółowy schemat XML, zobacz [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Różnice między plikami. ctc i. vsct  
 Chociaż znaczenie za tagi XML w pliku. vsct są takie same jak w przypadku przestarzałych plików. CTC, ich implementacja jest nieco inna.  
  
- Nowy **\<extern>** tag to miejsce, w którym można odwoływać się do innych plików h do skompilowania, takich jak te dla [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] paska narzędzi.  
  
- Chociaż pliki. vsct obsługują instrukcję **/include** , podobnie jak pliki CTC, funkcja zawiera również nowy \<**import> element * *. Różnica polega na tym, że **/include** zawiera **wszystkie** informacje, ale \<**import> * * tylko nazwy.  
  
- Pliki. CTC wymagają pliku nagłówkowego, w którym definiujesz dyrektywy preprocesora, jeden nie jest wymagany dla plików. vsct. Zamiast tego należy umieścić dyrektywy w tabeli symboli znajdujące się w **\<Symbol>** elementach znajdujących się w dolnej części pliku. vsct.  
  
- pliki. vsct oferują **\<Annotation>** tag, który umożliwia osadzanie dowolnych informacji, takich jak notatki lub obrazy.  
  
- Wartości są przechowywane jako atrybuty w elemencie.  
  
- Flagi poleceń można przechowywać pojedynczo lub na stosie.  Funkcja IntelliSense nie działa jednak w przypadku stosowych flag poleceń. Aby uzyskać więcej informacji na temat flag poleceń, zobacz [element flagi polecenia](../../extensibility/command-flag-element.md).  
  
- Można określić wiele typów, takich jak zwijanie list rozwijanych, kombi itd.  
  
- Identyfikatory GUID nie są weryfikowane.  
  
- Każdy element interfejsu użytkownika ma ciąg, który reprezentuje wyświetlany tekst.  
  
- Element nadrzędny jest opcjonalny. W przypadku pominięcia zostanie użyta wartość "Grupa nieznana".  
  
- Argument ikony jest opcjonalny.  
  
- Sekcja mapy bitowej — taka sama jak plik. CTC, z tą różnicą, że można teraz określić nazwę pliku za pośrednictwem href, która będzie pobierana przez kompilator vsct.exe w czasie kompilacji.  
  
- ResID — można używać starego identyfikatora zasobu mapy bitowej i nadal działa tak samo jak w plikach. CTC.  
  
- HRef — Nowa metoda, która umożliwia określenie nazwy pliku dla zasobu mapy bitowej. Przyjęto założenie, że wszystkie są używane, aby można było pominąć użytą sekcję. Kompilator najpierw szuka zasobów lokalnych dla pliku, a następnie w dowolnych udziałach sieciowych i wszystkich zasobach zdefiniowanych przez przełącznik/I.  
  
- Powiązanie klawiszy — nie trzeba już określać emulatora. Jeśli określisz, kompilator przyjmie, że edytor i emulator są takie same.  
  
- Keychord — został porzucony. Nowy format to Klucz1, MOD1, klucz2, Mod2.  Można określić znak, szesnastkowy lub VK.  
  
  Nowy kompilator vsct.exe, kompiluje pliki. ctc i. vsct. Stary kompilator ctc.exe nie będzie jednak rozpoznawać ani kompilować plików vsct.  
  
  Możesz użyć kompilatora vsct.exe, aby skonwertować istniejący plik. Dyrektor ds do pliku. vsct. Aby uzyskać więcej informacji na ten temat, zobacz [How to: Create a. Plik vsct z istniejącego. Plik dyrektor ds](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## <a name="the-vsct-file-elements"></a>Vsct — elementy pliku  
 Tabela poleceń ma następującą hierarchię i elementy:  
  
 [Element](../../extensibility/commandtable-element.md) () — reprezentuje wszystkie polecenia, grupy menu i menu skojarzone z pakietu VSPackage.  
  
 [Element extern](../../extensibility/extern-element.md) — odwołuje się do wszystkich zewnętrznych plików. h, które mają zostać scalone przy użyciu pliku. vsct.  
  
 [Include](../../extensibility/include-element.md) — zawiera wszystkie dodatkowe pliki nagłówka (. h), które chcesz skompilować wraz z plikiem. vsct. Plik. vsct może zawierać pliki. h zawierające stałe, które definiują polecenia, grupy menu i menu zapewniane przez środowisko IDE lub inne pakietu VSPackage.  
  
 [Commands](../../extensibility/commands-element.md) — reprezentuje wszystkie poszczególne polecenia, które mogą być wykonywane. Każde polecenie ma cztery następujące elementy podrzędne:  
  
 [Element menu](../../extensibility/menus-element.md) — reprezentuje wszystkie menu i paski narzędzi w pakietu VSPackage. Menu są kontenerami dla grup poleceń.  
  
 [Groups](../../extensibility/groups-element.md) — reprezentuje wszystkie grupy w pakietu VSPackage. Grupy są kolekcjami poszczególnych poleceń.  
  
 [Element Buttons](../../extensibility/buttons-element.md) — reprezentuje wszystkie przyciski poleceń i elementy menu w pakietu VSPackage. Przyciski są kontrolkami wizualnymi, które mogą być skojarzone z poleceniami.  
  
 [Element bitmaps](../../extensibility/bitmaps-element.md) — reprezentuje wszystkie mapy bitowe dla wszystkich przycisków w pakietu VSPackage. Mapy bitowe są obrazami wyświetlanymi obok lub na przyciskach poleceń, w zależności od kontekstu.  
  
 [CommandPlacements element](../../extensibility/commandplacements-element.md) — wskazuje dodatkowe lokalizacje, w których poszczególne polecenia powinny znajdować się w menu pakietu VSPackage.  
  
 [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) — określa, czy polecenie ma być wyświetlane przez cały czas, czy też tylko w niektórych kontekstach, na przykład gdy wyświetlane jest konkretne okno dialogowe lub okno. Menu i polecenia, które mają wartość dla tego elementu, będą wyświetlane tylko wtedy, gdy określony kontekst jest aktywny. Domyślnym zachowaniem jest wyświetlanie polecenia przez cały czas.  
  
 [Element powiązania](../../extensibility/keybindings-element.md) klawiszy — określa dowolne powiązania kluczy dla poleceń. Oznacza to, że co najmniej jedną kombinację klawiszy, którą należy nacisnąć, aby wykonać polecenie, takie jak **Ctrl + S**.  
  
 [UsedCommands](../../extensibility/usedcommands-element.md) — informuje o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] środowisku, że mimo że określone polecenie jest zaimplementowane przez inny kod, gdy bieżący pakietu VSPackage jest aktywny, udostępnia implementację poleceń.  
  
 `Symbols Element` — Zawiera nazwy symboli i identyfikatory GUID dla wszystkich poleceń w pakiecie.  
  
## <a name="vsct-file-design-guidelines"></a>. Wytyczne dotyczące projektowania plików vsct  
 Aby pomyślnie zaprojektować plik. vsct, postępuj zgodnie z poniższymi wskazówkami.  
  
- Polecenia można umieścić tylko w grupach, grupy można umieścić tylko w menu, a menu można umieścić tylko w grupach. W środowisku IDE są wyświetlane tylko menu, a nie są to grupy i polecenia.  
  
- Podmenu nie można bezpośrednio przypisywać do menu, ale muszą być przypisane do grupy, która jest z kolei przypisana do menu.  
  
- Polecenia, podmenu i grupy można przypisywać do jednej grupy nadrzędnej lub menu przy użyciu pola nadrzędnego definicji dyrektywy.  
  
- Organizowanie tabeli poleceń wyłącznie za pomocą pól nadrzędnych w dyrektywach ma znaczny limit. Dyrektywy definiujące obiekty mogą przyjmować tylko jeden argument nadrzędny.  
  
- Ponowne użycie poleceń, grup lub podmenu wymaga zastosowania nowej dyrektywy do utworzenia nowego wystąpienia obiektu z własną `GUID:ID` parą.  
  
- Każda `GUID:ID` para musi być unikatowa. Użycie polecenia, które ma na przykład zostać umieszczone w menu, na pasku narzędzi lub w menu kontekstowym, jest obsługiwane przez <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs.  
  
- Polecenia i podmenu można także przypisać do wielu grup, a grupy można przypisywać do wielu menu za pomocą [elementu Commands](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Informacje o pliku VSCT  
 Jeśli wprowadzisz zmiany w pliku. vsct po obu tych kompilacjach i umieścisz je w natywnej satelitarnej bibliotece DLL, należy uruchomić **devenv.exe/Setup/nosetupvstemplates**. Spowoduje to wymuszenie ponownego odczytania zasobów pakietu VSPackage określonych w rejestrze eksperymentalnym oraz wewnętrznej bazy danych, która [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ma zostać przetworzona.  
  
 Podczas opracowywania można tworzyć i rejestrować wiele projektów pakietu VSPackage w przypadku eksperymentalnych gałęzi rejestru, które mogą prowadzić do mylącego bałaganu w środowisku IDE. Aby rozwiązać ten problem, można zresetować program eksperymentalny do ustawień domyślnych, aby usunąć wszystkie zarejestrowane pakietów VSPackage i wszelkie zmiany, które mogły zostać wprowadzone do IDE. Aby zresetować pakiet eksperymentalny, użyj narzędzia CreateExpInstance.exe dołączonego do zestawu Visual Studio SDK. Można go znaleźć pod adresem  
  
 **% PROGRAMFILES (x86)% \ Visual Studio \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Uruchom narzędzie przy użyciu wiersza polecenia **CreateExpInstance/Reset**. Należy pamiętać, że to narzędzie usuwa z eksperymentalnego programu Hive wszystkie zarejestrowane pakietów VSPackage nie są zwykle instalowane z programem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md)
