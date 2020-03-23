---
title: Rozszerzanie wersji próbnej lub aktualizowanie licencji
description: Dowiedz się, jak rozszerzyć bezpłatną wersję próbną programu Visual Studio, użyć subskrypcji online lub klucza produktu, aby odblokować program Visual Studio i zaktualizować przestarzałą lub wygasłą licencję.
ms.date: 12/18/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 8e11d77a94c7c1d3d7b038ecea1a6c61646e371f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027578"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>Rozszerzanie wersji próbnej lub aktualizowanie licencji

Bezpłatną wersję próbną [programu Visual Studio Professional lub Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/compare/) można ocenić przez 30 dni. A jeśli się zalogujesz, możesz przedłużyć okres próbny do 90 dni. (Visual Studio Community jest bezpłatny bez okresu próbnego. Musisz jednak [logować się](signing-in-to-visual-studio.md) okresowo, aby [aktualizować licencję.)](#update-a-stale-license)

Aby kontynuować korzystanie z programu Visual Studio po zakończeniu okresu próbnego, odblokuj go za pomocą [subskrypcji online](#use-an-online-subscription) lub [klucza produktu](#enter-a-product-key).

## <a name="use-an-online-subscription"></a>Korzystanie z subskrypcji online

1. Wybierz przycisk **Zaloguj się w** prawym górnym rogu IDE (lub przejdź do ustawień**konta** **plików,** > aby otworzyć okno dialogowe **Ustawienia konta,** a następnie wybierz przycisk **Zaloguj** się).

1. Wprowadź poświadczenia dla konta Microsoft lub konta służbowego. Visual Studio znajduje subskrypcję programu Visual Studio lub organizację Azure DevOps skojarzoną z Twoim kontem.

> [!IMPORTANT]
> Program Visual Studio automatycznie wyszukuje skojarzone subskrypcje online po nawiązaniu połączenia z organizacją Programu Azure DevOps z okna narzędzia **Eksploratora zespołu.** Po nawiązaniu połączenia z organizacją Azure DevOps można zalogować się przy użyciu konta microsoft i pracy lub szkoły. Jeśli istnieje subskrypcja online dla tego konta użytkownika, visual studio automatycznie odblokuje IDE dla Ciebie.

Aby uzyskać więcej informacji na temat subskrypcji programu Visual Studio i ich działania, zobacz stronę [Często zadawane pytania dotyczące obsługi subskrypcji.](https://visualstudio.microsoft.com/subscriptions/support/)

## <a name="enter-a-product-key"></a>Wprowadzanie klucza produktu

1. Wybierz pozycję**Ustawienia konta** **plików,** > aby otworzyć okno dialogowe Ustawienia **konta,** a następnie wybierz łącze **Licencja z kluczem produktu.**

1. Wprowadź klucz produktu w podanym miejscu.

> [!TIP]
> Wersje wstępne programu Visual Studio nie mają kluczy produktu. Aby korzystać z wersji wstępnej, należy zalogować się do ide.

Aby uzyskać więcej informacji na temat kluczy produktów programu Visual Studio dla programu Visual Studio i jak je uzyskać, zobacz [Using klucze produktu w subskrypcji programu Visual Studio](/visualstudio/subscriptions/product-keys) strony.

## <a name="update-a-stale-license"></a>Aktualizowanie nieaktualizyjną licencję

W programie Visual Studio może zostać wyświetlony komunikat "Twoja licencja przestarzała się i musi zostać zaktualizowana".

![Komunikat o nieaktualizuje nieaktualną licencję programu Visual](../ide/media/vs2017_stale-license.png)

Ten komunikat wskazuje, że chociaż subskrypcja może nadal być prawidłowa, token licencji używany przez program Visual Studio do przechowywania subskrypcji na bieżąco nie został odświeżony. Visual Studio informuje, że licencja jest przestarzała z jednego z następujących powodów:

* Visual Studio nie jest używane lub nie masz połączenia z Internetem przez dłuższy okres czasu.
* Wyloguj się z programu Visual Studio.

Zanim token licencji przestarzałe, Visual Studio najpierw wyświetla komunikat ostrzegawczy, który prosi o ponowne wniesienie poświadczeń.

Jeśli nie ponownie wejdyć poświadczenia, token zaczyna się przestarzałe i **ustawienia konta** okno dialogowe informuje, ile dni pozostało przed wygaśnięciem tokenu. Po wygaśnięciu tokenu należy ponownie w kontynuować korzystanie z programu Visual Studio.

> [!Important]
> Jeśli używasz programu Visual Studio przez dłuższy czas w środowiskach z ograniczonym lub bez dostępu do Internetu, należy użyć klucza produktu, aby odblokować program Visual Studio, aby uniknąć przerw.

## <a name="update-an-expired-license"></a>Aktualizowanie wygasłej licencji

Jeśli subskrypcja wygasła i nie masz już praw dostępu do programu Visual Studio, należy odnowić subskrypcję lub dodać inne konto, które ma subskrypcję. Aby uzyskać więcej informacji na temat używanej licencji, przejdź do**sekcji Ustawienia konta** **plików** > i zapoznaj się z informacjami o licencji po prawej stronie okna dialogowego. Jeśli masz inną subskrypcję skojarzoną z innym kontem, dodaj to konto do listy **Wszystkie konta** po lewej stronie okna dialogowego, wybierając łącze **Dodaj konto.**

## <a name="get-support"></a>Uzyskiwanie pomocy technicznej

Czasami coś pójdzie nie tak. Jeśli wystąpi problem, oto kilka opcji pomocy technicznej:

* Zgłaszaj problemy z produktem za pomocą narzędzia [Zgłoś problem.](how-to-report-a-problem-with-visual-studio.md)
* Odpowiedzi na pytania dotyczące subskrypcji, kont i rozliczeń znajdziesz w [często zadawanych pytaniach dotyczących pomocy technicznej dotyczące subskrypcji.](https://visualstudio.microsoft.com/subscriptions/support/)

## <a name="see-also"></a>Zobacz też

* [Logowanie do programu Visual Studio](../ide/signing-in-to-visual-studio.md)
* [Porównanie wersji programu Visual Studio](https://visualstudio.microsoft.com/vs/compare/)
* [Dowiedz się więcej o subskrypcjach programu Visual Studio](/visualstudio/subscriptions/)
