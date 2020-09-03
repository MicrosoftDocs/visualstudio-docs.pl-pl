---
title: Słownik warunków programu MSBuild
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154840"
---
# <a name="msbuild-glossary"></a>Słownik programu MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Te warunki są używane do opisywania Microsoft Build Engine (MSBuild) i jego składników.

## <a name="glossary"></a>Słownik
 AssemblyFoldersEx

 Lokalizacja w rejestrze, w której dostawcy innych firm przechowują ścieżki dla każdej wersji platformy, która obsługuje, gdzie można znaleźć zestawy odwołań w czasie projektowania.

 przetwarzanie wsadowe

 Przetwarzanie wsadowe oznacza dzielenie elementów na różne kategorie znane jako *partie*, na podstawie metadanych elementów, a następnie uruchamianie obiektu docelowego lub zadania jednokrotnie przy użyciu każdej partii. Przetwarzanie wsadowe to odpowiednik programu MSBuild w konstrukcji pętli for-----------. Aby uzyskać więcej informacji, zobacz Tworzenie [pakietów wsadowych](../msbuild/msbuild-batching.md).

 Kompilacja — zakres

 Kompilacja-zakres opisuje obiekt MSBuild, na przykład właściwość globalną, która jest potencjalnie widoczna dla projektu i wszystkich projektów podrzędnych, które są tworzone w ramach kompilacji obejmującej wiele projektów.

 projekt podrzędny

 Zobacz *projekt, element podrzędny*.

 rozgrzewa

 Można zdefiniować warunkowo wiele elementów MSBuild; oznacza to, że `Condition` atrybut jest wyświetlany w elemencie. Zawartość elementów warunkowych jest ignorowana, jeśli warunek nie zostanie spełniony `true` . Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).

 Definicja, element

 Zobacz *definicję elementu*.

 Emituj element

 W fazie wykonywania kompilacji elementy mogą być tworzone lub modyfikowane przez zadania, które mają `Output` elementy podrzędne, które mają `ItemName` atrybut. Zadanie jest określane jako "Emituj" nowe elementy.

 Emituj Właściwość

 W fazie wykonywania kompilacji właściwości mogą być tworzone lub modyfikowane przez zadania, które mają `Output` elementy podrzędne, które mają `PropertyName` atrybut. Zadanie jest określane jako "Emituj" nową właściwość.

 Faza oceny

 Ocena to pierwsza faza kompilacji projektu. Wszystkie właściwości i elementy są oceniane w kolejności, w jakiej występują w projekcie. Zaimportowane projekty są oceniane w miarę ich napotkania w projekcie. Elementy docelowe i zadania nie są uruchamiane do momentu ukończenia fazy wykonywania, a wszystkie właściwości lub elementy, które byłyby deklarowane lub emitowane, są ignorowane podczas obliczania.

 Faza wykonywania

 Wykonanie to druga faza kompilacji projektu. Wybrane elementy docelowe zostały skompilowane, a zadania są uruchamiane. Właściwości i elementy można tworzyć lub modyfikować w porównaniu z ich wartościami oceny.

 Funkcja, właściwość

 Zobacz *Funkcja właściwości*.

 Funkcja, element

 Zobacz element funkcja.

 element

 Elementy są danymi wejściowymi do systemu kompilacji i są pogrupowane w typy elementów na podstawie ich nazw elementów. Elementy zazwyczaj reprezentują pliki. Ponieważ elementy są nazwane przez typ elementu, do którego należą, *element* warunków i *wartość elementu* mogą być używane zamiennie. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).

 definicja elementu

 Grupy definicji elementów zawierają definicje elementów, które dodają domyślne metadane do dowolnego typu elementu. Podobnie jak dobrze znane metadane, domyślne metadane są skojarzone ze wszystkimi elementami określonego typu elementu. Metadane domyślne można jawnie przesłonić w definicji elementu. Aby uzyskać więcej informacji, zobacz [definicje elementu](../msbuild/item-definitions.md).

 Item — funkcja

 Funkcje elementów pobierają informacje o elementach w projekcie. Te funkcje upraszczają pobieranie elementów DISTINCT () i są szybsze niż pętle w elementach. Istnieją funkcje do manipulowania ścieżkami i ciągami elementów. Aby uzyskać więcej informacji, zobacz [funkcje elementu](../msbuild/item-functions.md)

 metadane elementu

 Zobacz *Metadata, Item*.

 Typ elementu

 Typy elementów są nazwanymi elementami, które mogą być używane jako parametry zadań. Zadania używają wartości elementów do wykonania kroków procesu kompilacji. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).

 metadane, element

 Metadane elementu to kolekcja par nazwa-wartość, która jest skojarzona z elementem. Metadane zawierają opisowe informacje dla elementu i są opcjonalne, z wyjątkiem dobrze znanych metadanych. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).

 metadane, dobrze znane

 Dobrze znane metadane są metadanymi elementów tylko do odczytu, które są inicjowane przy użyciu wstępnie zdefiniowanej wartości. Dobrze znane metadane zawierają opisowe informacje dotyczące elementu, który odwołuje się do pliku. Na przykład wartość dobrze znanych metadanych o nazwie `FullPath` jest pełną ścieżką do pliku, do którego istnieje odwołanie. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).

 przeznaczanie dla wielu platform

 Możliwość dla aplikacji lub projektu zestawu przeznaczona dla wielu różnych środowisk CLR i platform z programu MSBuild oraz z Visual Studio.

 profil

 Podzbiór pełnej struktury. Służy do minimalizowania ilości, która musi zostać pobrana na komputer.

 plik projektu

 Plik projektu zawiera skrypt programu MSBuild, który kontroluje kompilację. Pliki projektu zwykle mają rozszerzenie pliku kończące się na "proj", takie jak. csproj lub. vbproj. Pliki projektu mogą importować pliki właściwości i pliki docelowe.

 property

 Właściwość to para klucz-wartość, która jest używana do kontrolowania procesu kompilacji. Aby uzyskać więcej informacji, zobacz [Właściwości programu MSBuild](msbuild-properties1.md).

 Właściwość, środowisko

 Właściwość Environment jest właściwością, która jest automatycznie inicjowana do wartości zmiennej środowiskowej systemowej o tej samej nazwie. Aby uzyskać więcej informacji, zobacz [Właściwości programu MSBuild](msbuild-properties1.md).

 plik właściwości

 Plik właściwości to plik projektu, który zawiera głównie grupy właściwości i grupy elementów, które kierują kompilację. Według Konwencji ma rozszerzenie pliku. props. Pliki właściwości są zwykle importowane na początku skojarzonych plików projektu.

 Właściwość, funkcja

 Funkcja właściwości to systemowa właściwość lub metoda, która może służyć do oceniania skryptów programu MSBuild. Metody właściwości mogą służyć do odczytywania czasu systemowego, porównywania ciągów, dopasowywania wyrażeń regularnych i wykonywania innych akcji. Aby uzyskać więcej informacji, zobacz [funkcje właściwości](../msbuild/property-functions.md).

 Funkcja właściwości, zagnieżdżona

 Funkcje właściwości mogą być połączone w celu tworzenia bardziej złożonych funkcji. Przykład:

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

 Aby uzyskać więcej informacji, zobacz [funkcje właściwości](../msbuild/property-functions.md).

 Właściwość, globalna

 Właściwość globalna to para klucz-wartość, która jest używana do kontrolowania procesu kompilacji. Właściwości globalne są ustawiane w wierszu polecenia lub przy użyciu `Properties` atrybutu [zadania programu MSBuild](../msbuild/msbuild-task.md)i nie można ich modyfikować w fazie oceny kompilacji. Aby uzyskać więcej informacji, zobacz [Właściwości programu MSBuild](msbuild-properties1.md).

 Właściwość, lokalna

 Właściwość lokalna to para klucz-wartość, która jest używana do kontrolowania procesu kompilacji. Ten termin służy tylko do odróżnienia właściwości, która nie jest właściwością globalną.

 Właściwość, rejestr

 Właściwość rejestru ma wartość, która jest ustawiana za pomocą specjalnej składni, która odczytuje wartość podklucza rejestru systemowego. Aby uzyskać więcej informacji, zobacz [Właściwości programu MSBuild](msbuild-properties1.md).

 Właściwość, zarezerwowane

 Właściwość zastrzeżona to para klucz-wartość, która jest używana do kontrolowania procesu kompilacji. Zastrzeżone właściwości są automatycznie inicjowane dla wstępnie zdefiniowanych wartości. Aby uzyskać więcej informacji, zobacz [Właściwości programu MSBuild](msbuild-properties1.md).

 zakres projektu

 Zakres projektu — opisuje obiekt MSBuild, na przykład lokalną właściwość, która jest widoczna tylko w zawierającym go pliku projektu i do wszelkich importowanych projektów.

 projekt, element podrzędny

 Projekt podrzędny jest tworzony przez zadanie MSBuild podczas kompilacji projektu. Ten nowy projekt jest elementem podrzędnym projektu, który zawiera lub importuje element docelowy zawierający zadanie programu MSBuild. Projekt podrzędny dziedziczy właściwości globalne projektu nadrzędnego, chyba że są modyfikowane przez `Properties` atrybut.

 lista redist

 Lista redystrybucyjna: Lista zestawów, które odpowiadają danej architekturze.

 zestaw odwołań

 Zestaw, który jest używany w czasie projektowania do tworzenia aplikacji. Zestaw odwołania może mieć rzeczywisty kod i interfejsy prywatne z niego usunięte, pozostawiając tylko metadane i interfejsy publiczne.

 Właściwość rejestru

 Zobacz *właściwości, rejestr*.

 obiektów

 Obiekty docelowe grupują się w określonej kolejności i ujawniają sekcje pliku projektu jako punkty wejścia do procesu kompilacji. Aby uzyskać więcej informacji, zobacz [targets](../msbuild/msbuild-targets.md).

 obiekt docelowy, kompilacja

 Zobacz Target, działa.

 cel, ocenianie

 Ze względu na kompilację przyrostową elementy docelowe muszą być analizowane pod kątem potencjalnych zmian właściwości i elementów. Nawet jeśli element docelowy jest pominięty, te zmiany muszą zostać wprowadzone. Ocenianie celu oznacza wykonanie tej analizy i dokonanie tych zmian. Aby uzyskać więcej informacji, zobacz [Kompilacje przyrostowe](../msbuild/incremental-builds.md).

 cel, wykonywanie

 Wykonanie celu oznacza ocenę i wykonanie wszystkich zadań, które nie mają warunków lub których warunki mają wartość true. Podczas kompilowania przyrostowego elementy docelowe mogą być pominięte lub wykonane, ale są zawsze oceniane. Aby uzyskać więcej informacji, zobacz Target, ocenianie.

 obiekt docelowy, uruchomiony

 Element docelowy, który ma warunek, którego wynikiem jest false, nie jest uruchamiany, czyli nie ma wpływu na kompilację. Elementy docelowe, które są wykonywane lub zostały pominięte. W obu przypadkach element docelowy jest oceniany. Aby uzyskać więcej informacji, zobacz Target, ocenianie.

 element docelowy, pomijanie

 Jeśli kompilacja przyrostowa ustali, że wszystkie pliki wyjściowe są aktualne, a następnie element docelowy zostanie pominięty, oznacza to, że element docelowy jest szacowany, ale zadania w ramach elementu docelowego nie są wykonywane. Aby uzyskać więcej informacji, zobacz Target, ocenianie.

 Moniker struktury docelowej

 Nazwa opisująca strukturę (np.. NETFramwork, Silverlight itp.), wersja i profil (na przykład klient, serwer itp.), które chcesz określić jako docelowe.

 Pakiet docelowy

 Lista zestawów, które są dystrybuowane z daną strukturą i zestawem zestawów referencyjnych dla tej struktury.

 plik docelowy

 Plik targets to plik projektu, który zawiera głównie elementy docelowe i zadania, które kierują kompilację. Według Konwencji ma rozszerzenie pliku targets. Pliki docelowe są zwykle importowane na końcu skojarzonych plików projektu.

 task

 Zadania są jednostkami kodu wykonywalnego, które są [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] używane przez projekty do wykonywania operacji kompilacji. Na przykład zadanie może kompilować pliki wejściowe lub uruchomić narzędzie zewnętrzne. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).

 transform

 Transformacja jest konwersją jeden do jednego z jednej kolekcji elementów na inną. Poza umożliwieniem projektowi konwersji kolekcji elementów, transformacja umożliwia obiektowi docelowemu znalezienie bezpośredniego mapowania między danymi wejściowymi i wyjściowymi. Aby uzyskać więcej informacji, zobacz [transformacje](../msbuild/msbuild-transforms.md).

 dobrze znane metadane

 Zobacz *metadane, dobrze znane*.

## <a name="see-also"></a>Zobacz też

- [MSBuild1](../msbuild/msbuild.md)