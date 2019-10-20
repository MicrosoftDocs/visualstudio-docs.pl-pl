---
title: Dostosowywanie funkcji IntelliSense dla RequireJS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 2be07ef8-9c08-444b-a21a-22a4fe6386a3
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 279ac7737460c90f86918ae673e8f64ef1215546
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665881"
---
# <a name="customizing-intellisense-for-requirejs"></a>Dostosowywanie funkcji IntelliSense dla RequireJS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Począwszy od Visual Studio 2013 Update 4, obsługiwane jest wsparcie dla popularnego pliku języka JavaScript RequireJS oraz modułu ładującego moduły. RequireJS ułatwia definiowanie zależności między modułami kodu i dynamiczne ładowanie modułów tylko wtedy, gdy jest to konieczne. Podczas pisania kodu JavaScript korzystającego z RequireJS, sugestie IntelliSense będą udostępniane dla modułów, do których odwołuje się definicja modułu lub do `require()` z poziomu kodu.

 Domyślnie program Visual Studio obsługuje bardzo podstawową konfigurację do obsługi RequireJS, ale jest powszechną metodą konfigurowania własnych niestandardowych ustawień konfiguracji (czyli do definiowania aliasów dla bibliotek). W tym temacie opisano różne sposoby dostosowywania programu Visual Studio do pracy z unikatowymi ustawieniami projektu.

 W tym temacie opisano, jak:

- Dostosowywanie RequireJS w projektach ASP.NET

- Dostosuj RequireJS w projektach JSProj, które są używane do kompilowania aplikacji Apache Cordova, aplikacji ze sklepu Windows i aplikacji HTML programu LightSwitch

## <a name="customize-requirejs-in-aspnet-projects"></a>Dostosowywanie RequireJS w projektach ASP.NET
 Obsługa RequireJS jest włączana automatycznie, gdy plik o nazwie Wymagaj. js jest przywoływany przez bieżący plik JavaScript (Aby uzyskać więcej informacji, zobacz sekcję określanie kontekstu IntelliSense w [języku JavaScript IntelliSense](../ide/javascript-intellisense.md)). W projektach ASP.NET odwołanie wymaga. js jest zwykle wykonywane przy użyciu dyrektywy///\<reference/> w pliku _references. js.

### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>Konfigurowanie atrybutu data-main w projekcie ASP.NET
 Aby precyzyjnie symulować sposób działania aplikacji po jej uruchomieniu, Edytor JavaScript musi wiedzieć, jaki plik powinien zostać załadowany jako pierwszy podczas konfigurowania wymaga. js. Jest to zazwyczaj skonfigurowane w pliku HTML aplikacji przy użyciu atrybutu `data-main` w elemencie skryptu, który odwołuje się do wymaga. js, jak pokazano poniżej.

```html
<script src="js/require.js" data-main="js/app.js"></script>
```

 W tym przykładzie skrypt, do którego odwołuje się data-main (js/App. js), jest ładowany natychmiast po wymaganiu. js. Plik, który jest ładowany natychmiast jest najlepszym miejscem, aby najpierw skonfigurować użycie RequireJS (przy użyciu `require.config()`). Aby poinformować Edytor JavaScript, jaki plik ma być używany do `data-main` w aplikacji, Dodaj atrybut `data-main`, a następnie zmodyfikuj dyrektywę///\<reference/>, która odwołuje się do pliku wymagane. js w aplikacji. Na przykład można użyć tej dyrektywy:

```javascript
/// <reference path="js/require.js" data-main="js/app.js" />
```

### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>Skonfiguruj stronę początkową aplikacji w projekcie ASP.NET
 Po uruchomieniu aplikacji RequireJS zakłada, że ścieżki względne do plików (na przykład ".. \\ "ścieżki" odnoszą się do pliku HTML, który załadował bibliotekę Wymagaj. js. Podczas pisania kodu w edytorze programu Visual Studio dla projektu ASP.NET, ta strona początkowa jest nieznana i należy poinformować Edytor o tym, co Strona początkowa ma używać w przypadku używania względnych ścieżek plików. Aby to zrobić, Dodaj atrybut `start-page` do dyrektywy///\<reference/>.

```javascript
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />
```

 Atrybut `start-page` określa adres URL strony, tak jak zobaczysz ją w przeglądarce podczas uruchamiania aplikacji.

## <a name="customize-requirejs-in-jsproj-projects"></a>Dostosowywanie RequireJS w projektach JSProj
 Projekty JSProj (pliki projektu kończące się rozszerzeniem. jsproj) są używane podczas kompilowania aplikacji dla Apache Cordova, aplikacji ze sklepu Windows opartych na języku HTML lub aplikacji HTML programu LightSwitch. W przeciwieństwie do projektów ASP.NET, te projekty odczytują odwołania do plików JS z plików HTML istniejących w projekcie. W związku z tym podczas edytowania kodu JavaScript w projekcie JSProj zostanie włączona obsługa RequireJS, jeśli aktualnie edytowany plik JavaScript jest przywoływany w innym pliku HTML, który odwołuje się również do programu Wymagaj. js.

 Kroki dostosowywania wymagane przez projekty ASP.NET nie są wymagane w pliku projektu JSProj. Oznacza to, że pliki skryptów używane przez atrybut `data-main` w tagu skryptu, do których odwołują się wymagania. js są ładowane automatycznie w celu skonfigurowania pliku Wymagaj. js. Plik HTML odwołujący się do wymaga. js jest również używany jako strona początkowa dla aplikacji.

## <a name="see-also"></a>Zobacz też
 [Funkcja IntelliSense dla języka JavaScript](../ide/javascript-intellisense.md)
