---
title: JavaScript
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-javascript
ms.topic: conceptual
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 778912c3149f9f146c01dbab15afa4fabeaa49b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852258"
---
# <a name="javascript-in-visual-studio"></a>Język JavaScript w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript to język pierwszej klasy w programie Visual Studio. Podczas pisania kodu w języku JavaScript w środowisku IDE programu Visual Studio można używać większości lub wszystkich standardowych ułatwień edycji (fragmenty kodu, technologia IntelliSense itd.). Można napisać kod JavaScript dla wielu typów i usług aplikacji.

 Aby uzyskać dokumentację referencyjną języka JavaScript, zobacz [JavaScript](https://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Określone wersje programu Visual Studio lub specjalne rozszerzenia programu Visual Studio mogą być wymagane do opracowania określonych typów i usług aplikacji przy użyciu języka HTML i języka JavaScript. Poniższa lista zawiera linki do dodatkowych informacji.

- Aby tworzyć aplikacje dla wielu platform przy użyciu Apache Cordova, [pobierz Visual Studio Tools dla Apache Cordova](https://taco.visualstudio.com/docs/install-vs-tools-apache-cordova/).

- Aby utworzyć [Sklep Windows](https://developer.microsoft.com/), [Windows Phone](https://developer.microsoft.com/)i aplikacje uniwersalne (obsługujące obie platformy), [Pobierz narzędzia](https://developer.microsoft.com/windows/downloads).

- Aby utworzyć usługi oparte na chmurze, zobacz [witrynę Microsoft Azure](https://azure.microsoft.com/documentation/).

- Aby tworzyć witryny sieci Web i aplikacje sieci Web, [zobacz witrynę ASP.NET](https://dotnet.microsoft.com/apps/aspnet/web-apps).

  > [!NOTE]
  > Można utworzyć pustą witrynę sieci Web ASP.Net i używać jej do programowania w języku HTML, CSS i JavaScript. Plik Webconfig dostarczony przez ASP.NET umożliwia debugowanie w programie Visual Studio (lub korzystanie z narzędzi F12 podczas uruchamiania aplikacji).

  Edytor kodu JavaScript w programie Visual Studio zapewnia obsługę technologii IntelliSense. Aby uzyskać więcej informacji, zobacz [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Co nowego w języku JavaScript
 Nowe funkcje języka JavaScript są wymienione w poniższej tabeli.

|Cechy|Opis|
|-------------|-----------------|
|Klasy|Nowa składnia obsługuje deklarację [klas](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/class).|
|Niesie obietnice zwiększenia|[Niesie obietnice zwiększenia](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) umożliwiają łatwiejsze i przejrzyste Kodowanie asynchroniczne. Obsługiwane są konstruktory Promise oraz `all` `race` metody narzędziowe i.|
|Iteratory|Teraz można wykonywać iteracje obiektów ITER (w tym tablic, obiektów przypominających tablicę i iteratorów), wywołując niestandardowy hak iteracji z instrukcjami, które mają być wykonane dla wartości każdej odrębnej właściwości. Aby uzyskać więcej informacji, zobacz [Iteratory i generatory](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Iterators_and_Generators). **Uwaga:**  Generatory nie są jeszcze obsługiwane.|
|Funkcje strzałek|Funkcja strzałka (=>) zawiera skróconą składnię `function` słowa kluczowego, która cechuje powiązanie leksykalne `this` .|
|Nowe metody dla obiektów wbudowanych|[Obiekt Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array), [obiekt matematyczny](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Math), [obiekt Number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number), [obiekt Object i](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)obiekty [typu String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String) zawierają wiele nowych funkcji i właściwości narzędzi do manipulowania i inspekcji danych.|
|Ulepszenia literałów obiektów|Obiekty obsługują teraz właściwości obliczane, zwięzłe definicje metod i składnię skróconą dla właściwości, których wartość jest inicjowana dla tej samej zmiennej o nazwie. Aby uzyskać więcej informacji, zobacz [Tworzenie obiektów](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object).|
|Proxy|[Serwery proxy](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Proxy) umożliwiają zachowanie niestandardowe obiektów.|
|Parametry REST|Parametry REST umożliwiają przyłączanie kolejnych argumentów w wywołaniu funkcji do tablicy. Aby uzyskać więcej informacji, zobacz [Functions](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function).|
|Operator rozproszenia|[Operator rozproszenia](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Spread_operator) ( `…` ) rozwija wyrażenia iterowania do poszczególnych argumentów. Na przykład `a.b(…array)` jest w przybliżeniu taka sama jak `a.b.apply(a, array)` .|
|Symbole|Obiekty [symboli](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Symbol) umożliwiają dodawanie właściwości do istniejących obiektów bez możliwości ingerencji z istniejącymi właściwościami obiektu, bez zamierzonej widoczności i bez innych nieskoordynowanych dodatków przez inny kod.|
|Ciągi szablonu|[Ciągi szablonów](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals) są literałami ciągów, które umożliwiają ocenianie i łączenie wyrażeń z literałem ciągu.|
|Ulepszenia Unicode|Wprowadzono ulepszenia obsługi standardu Unicode. Na przykład nowy format sekwencji unikowej obsługuje Astral punkty kodu (punkty kodu z więcej niż czterema cyframi szesnastkowymi). Aby uzyskać więcej informacji, zobacz [znaki specjalne](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions#Types_of_special_characters).|
|WeakSet|[WeakSet](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakSet) to kolekcja obiektów, które będą zbierane jako elementy bezużyteczne, jeśli nie są one używane w innych miejscach.|
