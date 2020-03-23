---
title: Fragmenty kodu dla R
description: Fragmenty kodu dla języka R w programie Visual Studio zapewniają skróty do szybkiego wstawiania bloków kodu o dowolnej długości, co pomaga uniknąć ponownego pisania podobnego kodu w kółko.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 05a21da94dd643b04cea94b7840ca26d9379cb5a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969459"
---
# <a name="code-snippets"></a>Fragmenty kodu

Fragmenty kodu w programie Visual Studio zapewniają skróty, aby szybko wstawić bloki kodu o dowolnej długości, co pomaga uniknąć ponownego pisania podobnego kodu w kółko. Narzędzia R dla programu Visual Studio (RTVS) dodać dziesiątki przydatnych fragmentów języka R do kolekcji programu Visual Studio.

Aby wstawić fragment kodu, wpisz skróconą nazwę fragmentu kodu (pod warunkiem intellisense), a następnie naciśnij **klawisz Tab,** aby wstawić.

Kilka prostych przykładów:

- następnie `=` Tab i RTVS rozszerza `<-` ją do operatora przypisania.
- następnie `>` Tab i RTVS rozszerza `%>%` ją operator rury.

Urywki mogą być czymś więcej niż tylko wypełnieniem postaci. Fragment kodu do odczytu pliku CSV `read.csv` z funkcją, na przykład, może zwolnić z konieczności zapamiętywania nazw lub parametrów:

![Animacja używania fragmentu kodu do wstawiania wywołania do pliku read.csv](media/code-snippet-expansion.gif)

W takim przypadku podczas `readc`pisania funkcja IntelliSense wyświetla listę uzupełnień. Wybranie tego zakończenia w rozwijanej i `readc` **naciśnięciu klawisza Tab** powoduje zaznaczenie opcji Tab i ponowne naciśnięcie **klawisza Tab** powoduje rozwinięcie fragmentu kodu. (Z tego powodu rozszerzenie fragmentu jest często traktowane jako "wpisz fragment kodu i naciśnij dwukrotnie tab"). W większości przypadków pierwsza karta kończy wybór IntelliSense, a druga karta wyzwala rozszerzenie.

Aby wyświetlić wszystkie dostępne fragmenty kodu, otwórz okno dialogowe**Menedżer urywków** **kodu narzędzi** > **(Ctrl**+**K**,**B**) i wybierz pozycję **R** dla **języka**. Rozwiń grupy i wybierz poszczególne fragmenty kodu, aby wyświetlić opis i tekst skrótu:

![Okno dialogowe urywki kodu dla R](media/code-snippet-dialog.png)

Aby utworzyć niestandardowe fragmenty kodu, postępując zgodnie z instrukcjami dotyczącymi [Instruktażu: Utwórz fragment kodu](../ide/walkthrough-creating-a-code-snippet.md). Ostatecznie fragment kodu jest tylko plikiem XML. Na przykład poniższy kod jest fragmentem kodu dla `>`operacji potoku (skrót):

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

Pliki XML dla wszystkich fragmentów kodu są instalowane z RTVS; Ścieżka zawiera pole **Lokalizacja** w **Menedżerze urywków kodu.** Można je również znaleźć w kodzie źródłowym RTVS na GitHub pod [src/Package/Impl/Urywki](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets).
