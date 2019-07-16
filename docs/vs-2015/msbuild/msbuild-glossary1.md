---
title: Słownik terminów MSBuild
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e84a7c3c7e402edb3c39ea247ea7efffce1b60df
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154840"
---
# <a name="msbuild-glossary"></a>Słownik programu MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Te warunki są używane do opisywania aparatu Microsoft Build Engine (MSBuild) i jego składników.

## <a name="glossary"></a>Słownik
 AssemblyFoldersEx

 Lokalizacja rejestru, której od innych dostawców przechowywać ścieżki dla każdej wersji platformy obsługują one, gdzie rozpoznawania czasu projektowania można sprawdzić szukać zestawów odwołań.

 przetwarzanie wsadowe

 Przetwarzanie wsadowe oznacza, że podział elementów na różne kategorie, znane jako *partie*zgodnie z metadanych elementu, a następnie uruchamiając docelowego lub zadanie raz przy użyciu każdej partii. Przetwarzanie wsadowe jest odpowiednikiem MSBuild--pętli konstrukcji. Aby uzyskać więcej informacji, zobacz [przetwarzania wsadowego](../msbuild/msbuild-batching.md).

 zakres kompilacji

 Zakres kompilacji opisuje obiekt, MSBuild, na przykład właściwość globalną, potencjalnie widocznej na projekt i żadne projekty podrzędne, które są tworzone w kompilacji wielu projektów.

 Projekt podrzędny

 Zobacz *projektu, podrzędne*.

 condition

 Warunkowo; można zdefiniować wiele elementów MSBuild oznacza to, że `Condition` atrybutu jest wyświetlany w elemencie. Zawartość elementów warunkowych jest ignorowana, chyba, że warunek to `true`. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).

 Definicja, element

 Zobacz *elementu definicji*.

 Dodaj element

 W fazie wykonywania kompilacji elementów można utworzone lub zmodyfikowane przez zadania, które mają podrzędnych `Output` elementy, które mają `ItemName` atrybutu. Zadanie jest nazywany "emisji" nowe elementy.

 Dodaj właściwość

 W fazie wykonanie procesu kompilacji, właściwości mogą utworzone lub zmodyfikowane przez zadania, które mają podrzędnych `Output` elementy, które mają `PropertyName` atrybutu. Zadanie jest nazywany "emisji" nowej właściwości.

 Faza oceny

 Ocena jest pierwszą fazę kompilacji projektu. Wszystkie właściwości i elementy są obliczane w kolejności, w jakiej występują w projekcie. Importowany projektów są oceniane, po ich napotkaniu w projekcie. Elementy docelowe i zadania nie są uruchamiane, dopóki fazę wykonywania i właściwości lub elementy będą one zadeklarować lub emisji, są ignorowane podczas obliczania wartości.

 Faza wykonania

 Wykonanie jest drugiej fazy kompilacji projektu. Wybrane elementy są tworzone i wykonywania zadań. Utworzone lub zmodyfikowane właściwości i elementy w porównaniu do ich wartości oceny.

 Funkcja, właściwość

 Zobacz *funkcji właściwości*.

 Funkcja elementu

 Można znaleźć elementu funkcji.

 element

 Elementy to wejścia do systemu kompilacji i są grupowane w typy elementów na podstawie ich nazw elementu. Elementy zazwyczaj reprezentują pliki. Ponieważ elementy są reprezentowane przez typ elementu należą one do warunków *elementu* i *wartość elementu* mogą być używane zamiennie. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).

 definicja elementu

 Grupach definicji elementów zawierają definicji elementów, które dodawać metadane domyślne do dowolnego typu elementu. Podobnie jak metadane dobrze znanego metadanych domyślny jest skojarzone z wszystkimi elementami typu określonego elementu. Metadane domyślne można jawnie przesłonić w definicji elementu. Aby uzyskać więcej informacji, zobacz [definicje elementu](../msbuild/item-definitions.md).

 Funkcja Item

 Funkcje elementów uzyskać informacje na temat elementów w projekcie. Te funkcje upraszczają pobierania elementów Distinct() i są szybsze niż elementy w pętli. Dostępne są funkcje do manipulowania ścieżki elementu i ciągów. Aby uzyskać więcej informacji, zobacz [funkcje elementów](../msbuild/item-functions.md)

 metadane elementu

 Zobacz *metadanych elementu*.

 Typ elementu

 Typy elementów są nazywane listy elementów, które mogą być używane jako parametry dla zadań. Zadania umożliwiają wartości elementu wykonaj kroki procesu kompilacji. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).

 metadane, element

 Metadane elementu jest kolekcją pary nazwa wartość, który jest skojarzony z elementem. Metadane informacje opisowe dla elementu i jest opcjonalny, z wyjątkiem dobrze znanych metadanych. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).

 metadane dobrze znanego

 Metadane dobrze znanego są metadane elementu tylko do odczytu, który jest inicjowany przy użyciu wstępnie zdefiniowanych wartości. Metadane dobrze znanego informacje opisowe dla elementu, który odwołuje się do pliku. Na przykład, wartość dobrze znanych metadanych o nazwie `FullPath` jest pełną ścieżką do pliku. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).

 przeznaczanie dla wielu platform

 Zdolność do aplikacji lub zestawu projekt przeznaczony dla wielu różnych CLR i struktury z programu MSBuild i Visual Studio.

 profile

 Podzbiór pełny framework. Służy to zminimalizować ilość, które muszą zostać pobrane na maszynę.

 plik projektu

 Plik projektu zawiera skrypt programu MSBuild, który kontroluje kompilacji. Pliki projektu zazwyczaj mają rozszerzenie pliku, który kończy się ciągiem "proj", takich jak .csproj lub .vbproj. Pliki projektu mogą importować pliki właściwości i pliki docelowe.

 property

 Właściwości to pary klucz wartość, która służy do kontrolowania procesu kompilacji. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](msbuild-properties1.md).

 właściwości, środowisko

 Właściwość środowiska jest właściwością, która jest inicjowana automatycznie wartość zmiennej środowiskowej systemu, który ma taką samą nazwę. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](msbuild-properties1.md).

 właściwości pliku

 Plik właściwości jest plik projektu, który zawiera głównie właściwości grup i grup, do których prowadzą kompilacji. Zgodnie z Konwencją ma ona, .props rozszerzenia pliku. Pliki właściwości zwykle są importowane na początku pliki skojarzonego projektu.

 Właściwość, funkcja

 Funkcja właściwości jest system właściwości lub metody, który może służyć do oceny, skryptów programu MSBuild. Metody właściwości mogą służyć do odczytywanie godziny systemowej, porównywanie ciągów, porównywanie wyrażeń regularnych i wykonywanie innych czynności. Aby uzyskać więcej informacji, zobacz [funkcji właściwości](../msbuild/property-functions.md).

 właściwości funkcji zagnieżdżonej

 Funkcje właściwości mogą być łączone do formularza bardziej złożone funkcje. Na przykład

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

 Aby uzyskać więcej informacji, zobacz [funkcji właściwości](../msbuild/property-functions.md).

 właściwości globalne

 Globalne właściwości to pary klucz wartość, która służy do kontrolowania procesu kompilacji. Globalne właściwości są ustawiane w wierszu polecenia lub przy użyciu `Properties` atrybutu [zadanie MSBuild](../msbuild/msbuild-task.md)i nie można modyfikować w fazie obliczania kompilacji. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](msbuild-properties1.md).

 właściwości lokalnej

 Właściwość lokalna jest parą klucz wartość, która służy do kontrolowania procesu kompilacji. Ten termin służy wyłącznie do właściwości, która nie jest właściwością globalną rozróżniania.

 Właściwość, rejestr

 Właściwości rejestru ma wartość ustawioną przy użyciu specjalnej składni, która odczytuje wartość podklucza rejestru systemu. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](msbuild-properties1.md).

 właściwości zastrzeżone

 Zastrzeżonych właściwości to pary klucz wartość, która służy do kontrolowania procesu kompilacji. Właściwości zastrzeżone są automatycznie inicjowane ze wstępnie zdefiniowanymi wartościami. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](msbuild-properties1.md).

 zakres projektu

 Zakres projektu opisuje obiekt, MSBuild, na przykład właściwości lokalnej, która jest widoczna tylko w pliku projektu zawierającego i wszelkich projektów, które importuje.

 Projekt, podrzędne

 Projekt podrzędny jest tworzony przez zadanie programu MSBuild podczas kompilacji projektu. Ten nowy projekt jest elementem podrzędnym elementu projektu, który zawiera lub importuje docelowy, który zawiera zadania programu MSBuild. Projekt podrzędny dziedziczy globalne właściwości projektu nadrzędnego, chyba że zostaną one zmienione przez `Properties` atrybutu.

 Lista REDIST

 Lista redystrybucyjna: listę zestawów, które odnoszą się do danej struktury.

 Odwołanie do zestawu

 Zestaw, który jest używany w czasie projektowania, tworzenia aplikacji. Zestaw odwołania może mieć rzeczywisty kod i interfejsów prywatnych, usunąć z niego, pozostawiając tylko metadane i interfejsów publicznych.

 właściwości rejestru

 Zobacz *właściwości, rejestr*.

 target

 Obiekt docelowy grupowanie zadań w określonej kolejności i udostępnia sekcje pliku projektu jako punkty wejścia do procesu kompilacji. Aby uzyskać więcej informacji, zobacz [cele](../msbuild/msbuild-targets.md).

 Wartość docelowa, tworzenie

 Zobacz obiektu docelowego, które są uruchomione.

 docelowe i ocena

 Ze względu na kompilację przyrostową elementów docelowych musi zostać przeanalizowany potencjalnych zmian właściwości i elementów. Nawet jeśli element docelowy jest pomijany, należy te zmiany. Oceny elementu docelowego oznacza, że wykonywanie tej analizy i wprowadzania tych zmian. Aby uzyskać więcej informacji, zobacz [kompilacje przyrostowe](../msbuild/incremental-builds.md).

 docelowe i wykonywanie

 Element docelowy wykonywania oznacza, że jej oceny i wykonywania wszystkich zadań, które nie mają żadnych warunków lub których warunki zostaną obliczone na wartość true. Podczas kompilacji przyrostowej obiekty docelowe może być pominięty lub wykonywane, ale są zawsze obliczane. Aby uzyskać więcej informacji, zobacz docelowych i oceny.

 docelowym systemem

 Obiekt docelowy, który zawiera warunek, który zwróci wartość false nie jest uruchamiane, oznacza to, nie ma wpływu na kompilację. Obiekty docelowe, które są uruchamiane, jest wykonywany czy pomijany. W obu przypadkach element docelowy jest oceniany. Aby uzyskać więcej informacji, zobacz docelowych i oceny.

 cel, pomijanie

 Jeśli kompilację przyrostową ustali, że wszystkie pliki wyjściowe są aktualne, a następnie element docelowy jest pomijany, oznacza to, element docelowy jest obliczane, ale zadania w ramach docelowej nie są wykonywane. Aby uzyskać więcej informacji, zobacz docelowych i oceny.

 moniker platformy docelowej

 Na nazwę opisującą platformę (np. NETFramwork, Silverlight, itp.), wersja i profil (na przykład klienta, serwer itp.), który ma zostać celem.

 targeting pack

 Lista zestawów, które są dystrybuowane przy użyciu danego framework i zestaw zestawów referencyjnych dla tej struktury.

 Plik docelowy

 Plik elementów docelowych to pliku projektu, który zawiera głównie elementy docelowe i zadania, które przeprowadzą kompilacji. Zgodnie z Konwencją ma .targets rozszerzenia pliku. Pliki docelowe zwykle są importowane z końcem pliki skojarzonego projektu.

 — zadanie

 Zadania to jednostki kodu wykonywalnego, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektów służy do wykonywania operacji kompilacji. Na przykład zadanie może skompilować pliki wejściowe lub uruchomić narzędzie zewnętrzne. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).

 transform

 Przekształcenia jest konwersją jeden do jednego, jeden element kolekcji do innego. Oprócz włączenia projektu do przekonwertowania kolekcji elementów, przekształcenia umożliwia docelowego w celu identyfikowania bezpośrednie mapowanie między ich dane wejściowe i wyjściowe. Aby uzyskać więcej informacji, zobacz [przekształca](../msbuild/msbuild-transforms.md).

 metadane dobrze znanego

 Zobacz *metadane dobrze znanego*.

## <a name="see-also"></a>Zobacz także

- [MSBuild1](../msbuild/msbuild.md)