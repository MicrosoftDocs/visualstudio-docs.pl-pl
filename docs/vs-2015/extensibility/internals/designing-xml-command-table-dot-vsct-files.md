---
title: Projektowanie tabeli poleceń XML (. Pliki Vsct) | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196848"
---
# <a name="designing-xml-command-table-vsct-files"></a>Projektowanie tabeli poleceń XML (. Pliki Vsct)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pliku XML polecenia tabeli (vsct) opisano układ i wygląd elementów polecenia dla pakietu VSPackage. Polecenie elementy obejmują przyciski, pola kombi, menu, paski narzędzi i grup elementów polecenia. W tym temacie opisano XML pliki tabeli poleceń, jak wpływają na elementy polecenia i menu oraz jak je utworzyć.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>Polecenia, menu, grup i pliku vsct  
 .vsct — pliki są zorganizowane wokół polecenia, menu i grup poleceń. Tagi XML w pliku vsct reprezentuje każdy z tych elementów, oraz innych skojarzonych elementów, takich jak przyciski poleceń, położenie polecenia i map bitowych.  
  
 Podczas tworzenia nowego pakietu VSPackage, uruchamiając [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] szablonu pakietu szablon generuje plik vsct niezbędne dla polecenia menu, okna narzędzi lub niestandardowy edytor, w zależności od wyborów. Następnie można zmodyfikować tego pliku vsct, aby spełniać wymagania określonego pakietu VSPackage. Przykłady sposobu modyfikowania pliku vsct, zobacz przykłady w [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).  
  
 Aby utworzyć pliku vsct nowy, pusty, zobacz [jak: Tworzenie. Pliku Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Po utworzeniu dodać elementy, atrybuty i wartości XML do pliku do opisywania układu elementu polecenia. Aby uzyskać szczegółowe schematu XML, zobacz [odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Różnice między plikami .ctc i vsct  
 Znaczenie za tagi XML w pliku vsct są takie same, zgodnie z programami znajdującymi się na obecnie przestarzały format pliku .ctc, ich wdrażania jest nieco inna.  
  
- Nowy  **\<extern >** tag jest, gdzie możesz się odwoływać inne pliki .h kompilację, takie jak te dla [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] paska narzędzi.  
  
- Gdy vsct pliki pomocy technicznej **/ include** instrukcji, jak pliki .ctc zawiera także funkcje nową \< **importowanie >** elementu. Różnica polega na tym, **/ include** wiąże **wszystkie** informacji, ale \< **importowania >** wiąże tylko nazwy.  
  
- Gdy pliki .ctc wymagają pliku nagłówka, w której definiujesz swoje dyrektywy preprocesora, jeden nie jest wymagane dla .vsct — pliki. Zamiast tego należy umieścić swoje dyrektywy w tabeli symboli znajduje się w  **\<Symbol >** elementów znajdujących się w dolnej części pliku vsct.  
  
- Funkcja pliki vsct  **\<adnotacja >** znacznik, który umożliwia osadzanie wszelkie informacje, które lubisz, takie jak informacje o lub nawet obrazy.  
  
- Wartości są przechowywane jako atrybuty w elemencie.  
  
- Flag poleceń mogą być przechowywane osobno lub skumulowany.  Funkcja IntelliSense, jednak nie działa na flag skumulowany poleceń. Aby uzyskać więcej informacji na temat flag poleceń, zobacz [Command Flag, Element](../../extensibility/command-flag-element.md).  
  
- Można określić wiele typów, takie jak podział listy rozwijane, combos itp.  
  
- Identyfikatory GUID nie sprawdzania poprawności.  
  
- Każdy element interfejsu użytkownika ma ciąg, który reprezentuje tekst, który jest wyświetlany z nim.  
  
- Nadrzędny jest opcjonalne. W przypadku pominięcia jest używana wartość "Nieznany grupy".  
  
- Ikona argument jest opcjonalny.  
  
- Sekcja mapy bitowej — taka sama jak .ctc pliku, z tą różnicą, że można teraz określić nazwę pliku, za pośrednictwem href, który będzie pobierany przez kompilator vsct.exe w czasie kompilacji.  
  
- ResID — stary identyfikator zasobu mapy bitowej mogą być używane i nadal działa tak samo jak w poniższym .ctc plików.  
  
- HRef — nową metodę, która pozwala określić nazwę pliku zasobu mapy bitowej. Przyjęto założenie, że wszystkie są używane, dzięki czemu można pominąć używanej sekcji. Kompilator wyszuka najpierw zasoby lokalne dla pliku, następnie na net udziałów, a wszelkie zasoby zdefiniowane przez przełącznik/i.  
  
- Powiązanie klawiszy — Nie trzeba już Określ emulator. Jeśli określono, kompilator zakłada, że edytor i emulatora są takie same.  
  
- Keychord — został porzucony. Nowy format jest klucz1, Mod1, klucz2, Mod2.  Można określić znak, szesnastkowo lub VK stałą.  
  
  Nowy kompilator, vsct.exe, kompiluje pliki vsct i .ctc. Stary kompilatora ctc.exe, jednak nie rozpoznaje ani nie Kompiluj .vsct — pliki.  
  
  Kompilator vsct.exe służy do konwertowania istniejącego pliku .cto do pliku vsct. Aby uzyskać więcej informacji na ten temat, zobacz [jak: Tworzenie. Plik Vsct z istniejącej. Dyrektor ds. technologii pliku](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## <a name="the-vsct-file-elements"></a>Elementy pliku vsct  
 Tabeli poleceń ma następujące hierarchii i elementy:  
  
 [CommandTable, Element](../../extensibility/commandtable-element.md) — reprezentuje wszystkie polecenia, grupy menu i menu skojarzone z pakietu VSPackage.  
  
 [Extern, Element](../../extensibility/extern-element.md) — odwołuje się do wszystkich plików zewnętrznych .h chcesz scalić przy użyciu pliku vsct.  
  
 [Umieść Element](../../extensibility/include-element.md) — odwołuje się do żadnych plików dodatkowych nagłówków (.h), które chcesz skompilować wraz z plikiem your.vsct. Pliku vsct może zawierać pliki .h zawierające stałe, które określają polecenia, grupy menu i menu, które zapewnia IDE lub innego pakietu VSPackage.  
  
 [Polecenia elementu](../../extensibility/commands-element.md) — reprezentuje wszystkie pojedynczych poleceń, które mogą być wykonywane. Każde polecenie ma następujących elementów podrzędnych cztery:  
  
 [Element menu](../../extensibility/menus-element.md) — reprezentuje wszystkie menu i paski narzędzi pakietu VSPackage. Menu są kontenerami dla grupy poleceń.  
  
 [Grupuje Element](../../extensibility/groups-element.md) — reprezentuje wszystkie grupy w pakietu VSPackage. Grupy są kolekcjami pojedynczych poleceń.  
  
 [Przyciski Element](../../extensibility/buttons-element.md) — reprezentuje wszystkie przyciski poleceń i elementów menu w pakietu VSPackage. Przyciski są visual formanty, które mogą być skojarzone z poleceniami.  
  
 [Bitmaps, Element](../../extensibility/bitmaps-element.md) — reprezentuje wszystkie mapy bitowe dla wszystkich przycisków z pakietu VSPackage. Mapy bitowe mają rozmiar obrazów wyświetlanych obok lub przycisków poleceń, w zależności od kontekstu.  
  
 [CommandPlacements, Element](../../extensibility/commandplacements-element.md) — dodatkowych lokalizacjach wskazuje, gdzie poszczególne polecenia powinien znajdować się w menu Twojego pakietu VSPackage.  
  
 [VisibilityConstraints, Element](../../extensibility/visibilityconstraints-element.md) — Określa, czy polecenie wyświetla przez cały czas lub tylko w niektórych kontekstach, np. gdy zostanie wyświetlona określonego okna dialogowego lub okna. Menu i poleceń, które mają wartość dla tego elementu spowoduje wyświetlenie tylko wtedy, gdy określony kontekst jest aktywny. Zachowanie domyślne jest do wyświetlenia polecenia przez cały czas.  
  
 [KeyBindings, Element](../../extensibility/keybindings-element.md) — Określa wszelkie powiązań klawiszy dla polecenia. Oznacza to, co najmniej jeden kombinacji klawiszy, które muszą zostać naciśnięte w celu wykonania tego polecenia, takie jak **CTRL + S**.  
  
 [UsedCommands, Element](../../extensibility/usedcommands-element.md) — Informs [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] środowiska, mimo że określone polecenie jest implementowany przez inny kod, gdy bieżącego pakietu VSPackage jest aktywny, zapewnia wykonania polecenia.  
  
 `Symbols Element` — Zawiera nazwy symboli i identyfikatory GUID dla wszystkich poleceń w pakiecie.  
  
## <a name="vsct-file-design-guidelines"></a>. Wytyczne dotyczące projektowania pliku Vsct  
 Aby pomyślnie zaprojektować pliku vsct, należy przestrzegać następujących wytycznych.  
  
- Polecenia można umieścić tylko w grupach, grup, które można umieścić tylko w menu i menu można umieścić tylko w grupach. W środowisku IDE programu grupy są wyświetlane tylko menu i poleceń nie jest.  
  
- Podmenu nie można przypisać bezpośrednio do menu, ale muszą być przypisane do grupy, która z kolei jest przypisany do menu.  
  
- Polecenia, menu podrzędne i grup można przypisać do jednej grupy element nadrzędny lub menu przy użyciu pola nadrzędnego ich definiujące dyrektywy.  
  
- Organizowanie tabeli polecenia wyłącznie za pośrednictwem pola nadrzędnego w dyrektywach ma znaczące ograniczenia. Dyrektywy definiujące obiekty, które może potrwać argument tylko jedną jednostkę nadrzędną.  
  
- Ponowne użycie poleceń, grup lub podmenu wymagane jest użycie nowej dyrektywy, aby utworzyć nowe wystąpienie obiektu za pomocą własnego `GUID:ID` pary.  
  
- Każdy `GUID:ID` pary muszą być unikatowe. Ponowne użycie polecenia, który na przykład został umieszczony w menu, pasek narzędzi lub menu kontekstowego, jest obsługiwane przez <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu.  
  
- Polecenia i podmenu również można przypisać do wielu grup i grup, które można przypisać do wielu menu przy użyciu [Commands, Element](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Informacje o pliku Vsct  
 Jeśli wprowadzisz zmiany w pliku vsct po zarówno skompilować go i umieść go w macierzystym satelitarną bibliotekę DLL, należy uruchomić **/nosetupvstemplates/Setup devenv.exe**. W ten sposób wymusza zasobów pakietu VSPackage, określone w doświadczalnych rejestr w celu należy przeczytać i wewnętrznej bazy danych, który opisuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] odbudowania.  
  
 Podczas tworzenia aplikacji możliwe jest dla wielu projektów pakietu VSPackage zostać utworzona i zarejestrowana w gałęzi rejestru eksperymentalnych, który może prowadzić do mylące nieładu w IDE. Aby rozwiązać ten problem, możesz zresetować eksperymentalne gałęzi do domyślnych ustawień do usuwania wszystkich zarejestrowanych pakietów VSPackage i wszelkie zmiany, które mogły zostać wprowadzone do środowiska IDE. Aby zresetować eksperymentalne hive, narzędzie CreateExpInstance.exe dostarczanego z Visual Studio SDK. Można znaleźć na stronie  
  
 **% PROGRAMFILES (x 86) %\Visual Studio \<wersji > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Uruchom narzędzie przy użyciu wiersza polecenia **/reset CreateExpInstance**. Należy pamiętać, że to narzędzie spowoduje usunięcie z doświadczalnych hive wszystkie zarejestrowane, nie jest zainstalowane przy użyciu pakietów VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md)
