---
title: Słownik programu MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f074bf7b5c7077b1c4808d7d3035be0c6366d526
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642719"
---
# <a name="msbuild-glossary"></a>Słownik programu MSBuild
Te warunki są używane do opisywania aparatu Microsoft Build Engine (MSBuild) i jego składników.

## <a name="glossary"></a>Słownik
 Lokalizacja w rejestrze AssemblyFoldersEx A której od innych dostawców przechowywać ścieżki dla każdej wersji platformy obsługują one, gdzie rozpoznawania czasu projektowania można sprawdzić szukać zestawów odwołań.

 Przetwarzanie wsadowe przetwarzania wsadowego oznacza podział elementów na różne kategorie, znane jako *partie*zgodnie z metadanych elementu, a następnie uruchamiając docelowego lub zadanie raz przy użyciu każdej partii. Przetwarzanie wsadowe jest odpowiednikiem MSBuild--pętli konstrukcji. Aby uzyskać więcej informacji, zobacz [przetwarzania wsadowego](../msbuild/msbuild-batching.md).

 zakres kompilacji kompilacji w zakresie opisuje obiekt, MSBuild, na przykład właściwość globalną, potencjalnie widocznej na projekt i żadne projekty podrzędne, które są tworzone w kompilacji wielu projektów.

 Projekt podrzędny zobacz *projektu, podrzędne*.

 warunek MSBuild wiele elementów, które mogą być definiowane warunkowo; oznacza to, że `Condition` atrybutu jest wyświetlany w elemencie. Zawartość elementów warunkowych jest ignorowana, chyba, że warunek to `true`. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).

 Definicja, zobacz element *elementu definicji*.

 Emituj elementu w fazie wykonanie procesu kompilacji, elementy mogą być utworzone lub zmodyfikowane przez zadania, które mają podrzędnych `Output` elementy, które mają `ItemName` atrybutu. Zadanie jest nazywany "emisji" nowe elementy.

 wyemitować właściwość w fazie wykonanie procesu kompilacji, właściwości mogą być utworzone lub zmodyfikowane przez zadania podrzędne `Output` elementy, które mają `PropertyName` atrybutu. Zadanie jest nazywany "emisji" nowej właściwości.

 Faza oceny, którą obliczenie jest pierwszą fazę kompilacji projektu. Wszystkie właściwości i elementy są obliczane w kolejności, w jakiej występują w projekcie. Importowany projektów są oceniane, po ich napotkaniu w projekcie. Elementy docelowe i zadania nie są uruchamiane, dopóki fazę wykonywania i właściwości lub elementy będą one zadeklarować lub emisji, są ignorowane podczas obliczania wartości.

 Faza wykonywania jest wykonywanie w drugiej fazy kompilacji projektu. Wybrane elementy są tworzone i wykonywania zadań. Utworzone lub zmodyfikowane właściwości i elementy w porównaniu do ich wartości oceny.

 Funkcja właściwości zobacz *funkcji właściwości*.

 Funkcja, element Zobacz elementu funkcji.

 element elementy to wejścia do systemu kompilacji i są grupowane w typy elementów na podstawie ich nazw elementu. Elementy zazwyczaj reprezentują pliki. Ponieważ elementy są reprezentowane przez typ elementu należą one do warunków *elementu* i *wartość elementu* mogą być używane zamiennie. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).

 grupach definicji elementów definicji elementu zawierają definicji elementów, które dodawać metadane domyślne do dowolnego typu elementu. Podobnie jak metadane dobrze znanego metadanych domyślny jest skojarzone z wszystkimi elementami typu określonego elementu. Metadane domyślne można jawnie przesłonić w definicji elementu. Aby uzyskać więcej informacji, zobacz [definicje elementów](../msbuild/item-definitions.md).

 Funkcje elementów funkcji elementu uzyskać informacje na temat elementów w projekcie. Te funkcje upraszczają pobierania elementów Distinct() i są szybsze niż elementy w pętli. Dostępne są funkcje do manipulowania ścieżki elementu i ciągów. Aby uzyskać więcej informacji, zobacz [elementu funkcji](../msbuild/item-functions.md)

 element metadanych zobacz *metadanych elementu*.

 Typ elementu typów elementów są nazywane listy elementów, które mogą być używane jako parametry dla zadań. Zadania umożliwiają wartości elementu wykonaj kroki procesu kompilacji. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).

 Metadane elementu metadanych elementu jest kolekcji pary nazwa wartość, który jest skojarzony z elementem. Metadane informacje opisowe dla elementu i jest opcjonalny, z wyjątkiem dobrze znanych metadanych. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).

 metadane dobrze znanego metadane dobrze znanego jest metadanych elementu tylko do odczytu, który jest inicjowany przy użyciu wstępnie zdefiniowanych wartości. Metadane dobrze znanego informacje opisowe dla elementu, który odwołuje się do pliku. Na przykład, wartość dobrze znanych metadanych o nazwie `FullPath` jest pełną ścieżką do pliku. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).

 wielowersyjność możliwości dla aplikacji lub zestawu projekt przeznaczony dla wielu różnych CLR i struktury z programu MSBuild i Visual Studio.

 Profil podzbiorem pełnej framework. Służy to zminimalizować ilość, które muszą zostać pobrane na maszynę.

 plik projektu plik projektu zawiera skrypt programu MSBuild, który kontroluje kompilacji. Pliki projektu zazwyczaj mają rozszerzenie pliku, która kończy się *proj*, takich jak *.csproj* lub *.vbproj*. Pliki projektu mogą importować pliki właściwości i pliki docelowe.

 Właściwość element właściwości to pary klucz wartość, która służy do kontrolowania procesu kompilacji. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).

 właściwości środowiska właściwość środowiska jest właściwością, która jest inicjowana automatycznie wartość zmiennej środowiskowej systemu, który ma taką samą nazwę. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).

 Plik właściwości pliku, A Właściwość jest plik projektu, który zawiera głównie właściwości grup i grup, do których prowadzą kompilacji. Zgodnie z Konwencją ma rozszerzenie pliku *.props*. Pliki właściwości zwykle są importowane na początku pliki skojarzonego projektu.

 Właściwość, funkcja właściwości funkcji jest system właściwości lub metody, który może służyć do oceny, skryptów programu MSBuild. Metody właściwości mogą służyć do odczytywanie godziny systemowej, porównywanie ciągów, porównywanie wyrażeń regularnych i wykonywanie innych czynności. Aby uzyskać więcej informacji, zobacz [funkcji właściwości](../msbuild/property-functions.md).

 Funkcja właściwości funkcji zagnieżdżonych właściwości mogą być łączone do utworzenia bardziej złożone funkcje. Na przykład

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

 Aby uzyskać więcej informacji, zobacz [funkcji właściwości](../msbuild/property-functions.md).

 właściwości globalne, globalny właściwości to pary klucz wartość, która służy do kontrolowania procesu kompilacji. Globalne właściwości są ustawiane w wierszu polecenia lub przy użyciu `Properties` atrybutu [zadanie MSBuild](../msbuild/msbuild-task.md)i nie można modyfikować w fazie obliczania kompilacji. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).

 Właściwość, lokalnego lokalnych właściwości to pary klucz wartość, która służy do kontrolowania procesu kompilacji. Ten termin służy wyłącznie do właściwości, która nie jest właściwością globalną rozróżniania.

 Właściwość, właściwości rejestru rejestru ma wartość, która jest ustawiona przy użyciu specjalnej składni, która odczytuje wartość podklucza rejestru systemu. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).

 właściwości zastrzeżone zastrzeżonych właściwości to pary klucz wartość, która służy do kontrolowania procesu kompilacji. Właściwości zastrzeżone są automatycznie inicjowane ze wstępnie zdefiniowanymi wartościami. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).

 zakres projektu zakresu projektu opisuje obiekt, MSBuild, na przykład właściwości lokalnej, która jest widoczna tylko w pliku projektu zawierającego i wszelkich projektów, które importuje.

 Projekt, projekt podrzędny element podrzędny jest tworzony przez zadanie programu MSBuild podczas kompilacji projektu. Ten nowy projekt jest elementem podrzędnym elementu projektu, który zawiera lub importuje docelowy, który zawiera zadania programu MSBuild. Projekt podrzędny dziedziczy globalne właściwości projektu nadrzędnego, chyba że zostaną one zmienione przez `Properties` atrybutu.

 Lista redystrybucyjna Lista REDIST: listę zestawów, które odnoszą się do danej struktury.

 Odwołanie do zestawu zestawu, który jest używany w czasie projektowania, tworzenia aplikacji. Zestaw odwołania może mieć rzeczywisty kod i interfejsów prywatnych, usunąć z niego, pozostawiając tylko metadane i interfejsów publicznych.

 właściwości rejestru zobacz *właściwości, rejestr*.

 docelowe A Grupowanie zadań w określonej kolejności i udostępnia sekcje pliku projektu jako punkty wejścia do procesu kompilacji. Aby uzyskać więcej informacji, zobacz [cele](../msbuild/msbuild-targets.md).

 cel tworzenia See, uruchomione.

 obiekt docelowy, ocenianie, ze względu na kompilację przyrostową, obiektów docelowych musi zostać przeanalizowany potencjalnych zmian właściwości i elementów. Nawet jeśli element docelowy jest pomijany, należy te zmiany. Oceny elementu docelowego oznacza, że wykonywanie tej analizy i wprowadzania tych zmian. Aby uzyskać więcej informacji, zobacz [kompilacje przyrostowe](../msbuild/incremental-builds.md).

 cel, wykonywania, wykonanie obiektu docelowego oznacza, że jej oceny i wykonywania wszystkich zadań, które nie mają żadnych warunków lub których warunki zostaną obliczone na wartość true. Podczas kompilacji przyrostowej obiekty docelowe może być pominięty lub wykonywane, ale są zawsze obliczane. Aby uzyskać więcej informacji, zobacz docelowych i oceny.

 docelowym systemem obiektu docelowego, który zawiera warunek, który zwróci wartość false nie jest uruchamiane, oznacza to, nie ma wpływu na kompilację. Obiekty docelowe, które są uruchamiane, jest wykonywany czy pomijany. W obu przypadkach element docelowy jest oceniany. Aby uzyskać więcej informacji, zobacz docelowych i oceny.

 obiekt docelowy zostanie pominięta, jeżeli kompilacja przyrostowa określa wszystkie pliki wyjściowe są aktualne, a następnie element docelowy jest pomijany, oznacza to, element docelowy jest oceniany, że zadania w ramach docelowej nie są wykonywane. Aby uzyskać więcej informacji, zobacz docelowych i oceny.

 moniker struktury na nazwę opisującą (np struktura docelowa. NETFramework, Silverlight, itp.), wersja i profil (na przykład klienta, serwer itp.), który ma zostać celem.

 targeting pack listę zestawów, które są dystrybuowane wraz z danym framework i zestaw zestawów referencyjnych dla tej struktury.

 obiekty docelowe A cele plik jest plik projektu, który zawiera głównie elementy docelowe i zadania, które przeprowadzą kompilacji. Zgodnie z Konwencją ma rozszerzenie pliku *.targets*. Pliki docelowe zwykle są importowane z końcem pliki skojarzonego projektu.

 zadanie zadania to jednostki kodu wykonywalnego, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektów służy do wykonywania operacji kompilacji. Na przykład zadanie może skompilować pliki wejściowe lub uruchomić narzędzie zewnętrzne. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).

 Przekształć element transformacja jest jeden do jednego konwersja jednego elementu kolekcji do innego. Oprócz włączenia projektu do przekonwertowania kolekcji elementów, przekształcenia umożliwia docelowego w celu identyfikowania bezpośrednie mapowanie między ich dane wejściowe i wyjściowe. Aby uzyskać więcej informacji, zobacz [przekształca](../msbuild/msbuild-transforms.md).

 metadane dobrze znanego zobacz *metadane dobrze znanego*.

## <a name="see-also"></a>Zobacz także
- [MSBuild](../msbuild/msbuild.md)