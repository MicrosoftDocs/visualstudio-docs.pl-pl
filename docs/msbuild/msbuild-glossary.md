---
title: Słowniczek MSBuild
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f20fdb4cd809e422bc33535f3143b45db99842f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633346"
---
# <a name="msbuild-glossary"></a>Słowniczek MSBuild

Terminy te są używane do opisywania aparatu kompilacji firmy Microsoft (MSBuild) i jego składników.

## <a name="glossary"></a>Słownik

AssemblyFoldersEx\
Lokalizacja rejestru, w której dostawcy innych firm przechowują ścieżki dla każdej wersji struktury, która obsługuje, gdzie rozdzielczość czasu projektowania może wyglądać, aby znaleźć zestawy odwołań.

dozowanie partii\
Przetwarzanie wsadowe oznacza dzielenie elementów na różne kategorie znane jako *partie*, na podstawie metadanych elementu, a następnie uruchamianie obiektu docelowego lub zadania jeden raz przy użyciu każdej partii. Przetwarzanie wsadowe jest odpowiednikiem MSBuild konstrukcji for-loop. Aby uzyskać więcej informacji, zobacz [Batching](../msbuild/msbuild-batching.md).

build-scope\
Zakres kompilacji opisuje obiekt MSBuild, na przykład właściwość globalną, która jest potencjalnie widoczna dla projektu i dla wszystkich projektów podrzędnych, które są tworzone w kompilacji wielu projektów.

projekt podrzędny\
Zobacz *projekt, dziecko*.

warunek\
Wiele elementów MSBuild można zdefiniować warunkowo; oznacza to, `Condition` że atrybut pojawia się w elemencie. Zawartość elementów warunkowych jest ignorowana, chyba `true`że warunek zostanie obliczony na . Aby uzyskać więcej informacji, zobacz [Warunki](../msbuild/msbuild-conditions.md).

definicja, pozycja\
Zobacz *definicję elementu*.

emituj element\
Podczas fazy wykonywania kompilacji elementy mogą być tworzone lub modyfikowane przez zadania, które mają elementy podrzędne, `Output` które mają `ItemName` atrybut. Zadanie mówi się, że "emitują" nowe elementy.

emituj nieruchomość\
Podczas fazy wykonywania kompilacji właściwości mogą być tworzone lub modyfikowane `Output` przez zadania, które mają elementy podrzędne, które mają `PropertyName` atrybut. Zadanie mówi się "emitować" nową właściwość.

faza oceny\
Ocena jest pierwszą fazą kompilacji projektu. Wszystkie właściwości i elementy są oceniane w kolejności, w jakiej pojawiają się w projekcie. Importowane projekty są oceniane w miarę ich napotkania w projekcie. Obiekty docelowe i zadania nie są uruchamiane do fazy wykonywania, a wszystkie właściwości lub elementy, które deklarują lub emitują, są ignorowane podczas oceny.

faza wykonania\
Wykonanie jest drugą fazą kompilacji projektu. Wybrane obiekty docelowe są budowane i wykonywane są zadania. Właściwości i elementy mogą być tworzone lub modyfikowane w porównaniu z ich wartości ewaluacji.

funkcja, właściwość\
Zobacz *funkcję właściwości*.

funkcja, pozycja\
Zobacz funkcję elementu.

szt.
Elementy są dane wejściowe do systemu kompilacji i są pogrupowane w typy elementów na podstawie ich nazwy elementów. Elementy zazwyczaj reprezentują pliki. Ponieważ towary są nazwane przez typ towaru, do którego należą, *terminy towar i* *wartość towaru* mogą być używane zamiennie. Aby uzyskać więcej informacji, zobacz [Elementy](../msbuild/msbuild-items.md).

definicja elementu\
Grupy definicji elementów zawierają definicje elementów, które dodają domyślne metadane do dowolnego typu elementu. Podobnie jak dobrze znane metadane, domyślne metadane są skojarzone ze wszystkimi elementami określonego typu elementu. Domyślne metadane mogą być jawnie zastąpione w definicji elementu. Aby uzyskać więcej informacji, zobacz [Definicje elementów](../msbuild/item-definitions.md).

item, funkcja\
Funkcje elementu uzyskać informacje o elementach w projekcie. Te funkcje upraszczają uzyskiwanie elementów Distinct() i są szybsze niż zapętlanie elementów. Istnieją funkcje do manipulowania ścieżkami elementów i ciągami. Aby uzyskać więcej informacji, zobacz [Funkcje elementu](../msbuild/item-functions.md).

metadane elementu\
Zobacz *metadane, element*.

typ przedmiotu\
Typy elementów są nazwane listy elementów, które mogą być używane jako parametry dla zadań. Zadania używają wartości elementu do wykonywania kroków procesu kompilacji. Aby uzyskać więcej informacji, zobacz [Elementy](../msbuild/msbuild-items.md).

metadane, element\
Metadane elementu to zbiór par nazwa-wartość, która jest skojarzona z elementem. Metadane zawiera opisowe informacje dla elementu i jest opcjonalny, z wyjątkiem dobrze znanych metadanych. Aby uzyskać więcej informacji, zobacz [Elementy](../msbuild/msbuild-items.md).

metadane, dobrze znane\
Dobrze znane metadane są metadanymi elementu tylko do odczytu, które są inicjowane przy użyciu wstępnie zdefiniowanej wartości. Dobrze znane metadane zawierają informacje opisowe dla elementu, który odwołuje się do pliku. Na przykład wartość dobrze znanych metadanych `FullPath` o nazwie jest pełna ścieżka pliku, do którego istnieje odwołanie. Aby uzyskać więcej informacji, zobacz [Elementy](../msbuild/msbuild-items.md).

multitargeting\
Możliwość projektu aplikacji lub zestawu do kierowania wiele różnych CLR i struktur z MSBuild i visual studio.

profil\
Podzbiór pełnej struktury. Służy to do zminimalizowania kwoty, która musi zostać pobrana na komputer.

plik projektu\
Plik projektu zawiera skrypt MSBuild, który steruje kompilacją. Pliki projektu zazwyczaj mają rozszerzenie pliku, które kończy się *proj*, takich jak *.csproj* lub *.vbproj*. Pliki projektu mogą importować pliki właściwości i pliki docelowe.

właściwość\
Właściwość jest parą klucz-wartość, która jest używana do kontrolowania procesu kompilacji. Aby uzyskać więcej informacji, zobacz [WŁAŚCIWOŚCI MSBuild](../msbuild/msbuild-properties.md).

właściwość, środowisko\
Właściwość environment jest właściwością, która jest automatycznie inicjowana do wartości zmiennej środowiskowej systemu, która ma taką samą nazwę. Aby uzyskać więcej informacji, zobacz [WŁAŚCIWOŚCI MSBuild](../msbuild/msbuild-properties.md).

plik właściwości\
Plik właściwości jest plikiem projektu, który zawiera głównie grupy właściwości i grupy elementów, które prowadzą kompilację. Zgodnie z konwencją, Ma rozszerzenie pliku *.props*. Pliki właściwości są zazwyczaj importowane na początku skojarzonych plików projektu.

właściwość, funkcja\
Funkcja właściwości jest właściwością systemową lub metodą, która może służyć do oceny skryptów MSBuild. Metody właściwości mogą służyć do odczytu czasu systemowego, porównywania ciągów, dopasowywania wyrażeń regularnych i wykonywania innych akcji. Aby uzyskać więcej informacji, zobacz [Funkcje właściwości](../msbuild/property-functions.md).

funkcja właściwości, zagnieżdżona\
Funkcje właściwości mogą być łączone w celu utworzenia bardziej złożonych funkcji. Na przykład:

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

Aby uzyskać więcej informacji, zobacz [Funkcje właściwości](../msbuild/property-functions.md).

nieruchomość, globalna\
Właściwość globalna jest parą klucz-wartość, która jest używana do kontrolowania procesu kompilacji. Właściwości globalne są ustawiane w wierszu `Properties` polecenia lub przy użyciu atrybutu [zadania MSBuild](../msbuild/msbuild-task.md)i nie mogą być modyfikowane podczas fazy oceny kompilacji. Aby uzyskać więcej informacji, zobacz [WŁAŚCIWOŚCI MSBuild](../msbuild/msbuild-properties.md).

nieruchomość, lokalna\
Właściwość lokalna jest parą klucz-wartość, która służy do kontrolowania procesu kompilacji. Termin ten jest używany tylko do odróżnienia właściwości, która nie jest właściwością globalną.

właściwość, rejestr\
Właściwość rejestru ma wartość ustawioną przy użyciu specjalnej składni, która odczytuje wartość podklucza rejestru systemowego. Aby uzyskać więcej informacji, zobacz [WŁAŚCIWOŚCI MSBuild](../msbuild/msbuild-properties.md).

nieruchomość, zastrzeżona\
Właściwość zastrzeżona jest parą klucz-wartość, która służy do kontrolowania procesu kompilacji. Właściwości zarezerwowane są inicjowane automatycznie do wstępnie zdefiniowanych wartości. Aby uzyskać więcej informacji, zobacz [WŁAŚCIWOŚCI MSBuild](../msbuild/msbuild-properties.md).

zakres projektu\
Zakres projektu opisuje obiekt MSBuild, na przykład właściwość lokalną, która jest widoczna tylko w pliku zawierającego projekt i dla wszystkich projektów, które importuje.

projekt, dziecko\
Projekt podrzędny jest tworzony przez zadanie MSBuild podczas kompilacji projektu. Ten nowy projekt jest elementem podrzędnym projektu, który zawiera lub importuje obiekt docelowy, który zawiera zadanie MSBuild. Projekt podrzędny dziedziczy właściwości globalne projektu nadrzędnego, chyba że `Properties` są one modyfikowane przez atrybut.

lista redist\
Lista redystrybucji: lista zestawów, które odpowiadają danej ramie.

zestaw referencyjny\
Złożenie, który jest używany w czasie projektowania do tworzenia aplikacji. Zestaw odwołań może mieć rzeczywisty kod i interfejsy prywatne usunięte z niego, pozostawiając tylko metadane i interfejsy publiczne.

właściwość rejestru\
Zobacz *właściwość, rejestr*.

cel\
Obiekt docelowy grupuje zadania w określonej kolejności i udostępnia sekcje pliku projektu jako punkty wejścia w procesie kompilacji. Aby uzyskać więcej informacji, zobacz [Cele](../msbuild/msbuild-targets.md).

cel, budynek\
Zobacz cel, działa.

cel, ocena\
Ze względu na kompilacji przyrostowej cele muszą być analizowane pod kątem potencjalnych zmian właściwości i elementów. Nawet jeśli cel zostanie pominięty, te zmiany muszą zostać wprowadzone. Ocena celu oznacza przeprowadzenie tej analizy i wprowadzenie tych zmian. Aby uzyskać więcej informacji, zobacz [Kompilacje przyrostowe](../msbuild/incremental-builds.md).

cel, wykonywanie\
Wykonanie obiektu docelowego oznacza jego ocenę i wykonanie wszystkich zadań, które nie mają żadnych warunków lub których warunki są zgodne z prawdą. Podczas kompilacji przyrostowej obiekty docelowe mogą być pomijane lub wykonywane, ale są one zawsze oceniane. Aby uzyskać więcej informacji, zobacz target, oceny.

cel, bieganie\
Obiekt docelowy, który ma warunek, który ocenia false nie jest uruchamiany, oznacza to, że nie ma wpływu na kompilacji. Obiekty docelowe, które są uruchamiane są wykonywane lub pomijane. W obu przypadkach cel jest oceniany. Aby uzyskać więcej informacji, zobacz target, oceny.

cel, pomijanie\
Jeśli kompilacja przyrostowa określa, że wszystkie pliki wyjściowe są aktualne, a następnie miejsce docelowe jest pomijany, oznacza to, że cel jest oceniany, ale zadania w obrębie obiektu docelowego nie są wykonywane. Aby uzyskać więcej informacji, zobacz target, oceny.

moniker struktury docelowej\
Nazwa opisująca strukturę (na przykład . NETFramework, Silverlight itp.), wersję i profil (na przykład klient, serwer itp.), na które chcesz kierować reklamy.

pakiet kierowania\
Lista zestawów, które są dystrybuowane z danej struktury i zestaw zestawów odwołań dla tej struktury.

plik obiektów docelowych\
Plik docelowy to plik projektu, który zawiera głównie obiekty docelowe i zadania, które kierują kompilacją. Zgodnie z konwencją, Ma rozszerzenie pliku *.targets*. Pliki docelowe są zazwyczaj importowane na końcu skojarzonych plików projektu.

zadanie\
Zadania są jednostkami kodu wykonywalnego, które projekty MSBuild używają do wykonywania operacji kompilacji. Na przykład zadanie może skompilować pliki wejściowe lub uruchomić narzędzie zewnętrzne. Aby uzyskać więcej informacji, zobacz [Zadania](../msbuild/msbuild-tasks.md).

transformacja\
Transformacja jest konwersją jeden do jednego z jednej kolekcji elementów do innej. Oprócz włączania projektu do konwersji kolekcji towarów, transformacja umożliwia miejsce docelowe do identyfikowania bezpośredniego mapowania między jego danych wejściowych i wyjściowych. Aby uzyskać więcej informacji, zobacz [Przekształcenia](../msbuild/msbuild-transforms.md).

dobrze znane metadane\
Zobacz *metadane, dobrze znane*.

## <a name="see-also"></a>Zobacz też

- [Msbuild](../msbuild/msbuild.md)
