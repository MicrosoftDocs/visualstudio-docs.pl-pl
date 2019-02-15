---
title: Używanie modeli w procesie tworzenia aplikacji
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, using models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aced2be4d584fb2ede58527a1d541f24089f220d
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315810"
---
# <a name="use-models-in-your-development-process"></a>Używanie modeli w procesie tworzenia aplikacji

W programie Visual Studio można użyć modelu, aby pomóc Ci zrozumieć i zmienić systemu, aplikacji lub składnika. Model może pomóc w wizualizacji na świecie, w którym działa system, wyjaśnienia potrzeb użytkowników, zdefiniuj architekturze systemu, analizowanie kodu i upewnij się, że Twój kod spełnia wymagania. Zobacz [wideo Channel 9: Poprawa architektury poprzez modelowanie](http://go.microsoft.com/fwlink/?LinkID=252078).

Aby zobaczyć, które wersje programu Visual Studio obsługuje każdy typ modelu, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Modele mogą pomóc na kilka sposobów:

- Rysowanie diagramów modelowania pomaga wyjaśnienie pojęcia związane z wymaganiami, architektury i projektowania wysokiego poziomu. Aby uzyskać więcej informacji, zobacz [modelowanie wymagań użytkowników](../modeling/model-user-requirements.md).

- Praca z modelami może pomóc w ujawnić niespójności w wymaganiach.

- Podczas komunikowania się z modelami pomaga przekazać ważne pojęcia poniżej ambiguously za pomocą języka naturalnego. Aby uzyskać więcej informacji, zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).

- Czasami służy modeli do generowania kodu lub inne artefakty, takie jak schematy bazy danych lub dokumentów. Na przykład składniki modelowania programu Visual Studio są generowane na podstawie modelu. Aby uzyskać więcej informacji, zobacz [Generowanie i konfigurowanie aplikacji na podstawie modeli](../modeling/generate-and-configure-your-app-from-models.md).

Można używać modeli, w wielu różnych procesów w ekstremalnych procedury agile wysoki.

## <a name="use-models-to-reduce-ambiguity"></a>Używanie modeli, aby ograniczyć niejednoznaczność

Język modelowania jest mniej niejednoznaczna niż języka naturalnego i jest przeznaczony do realizowania pomysłów, zwykle wymagana podczas tworzenia oprogramowania.

Jeżeli projekt zawiera małego zespołu po zwinnego wytwarzania oprogramowania, można użyć modele, aby pomóc w określeniu przypadków użycia. W dyskusji u klienta dotyczące ich wymagań Tworzenie modelu można wygenerować pytania znacznie szybciej, a także w szerszym obszaru produktu, niż pisania kodu skokiem lub prototypu.

Jeśli projekt jest duży i obejmuje zespoły w różnych częściach globu, można użyć modeli ułatwiających komunikację wymagania i architektury znacznie bardziej efektywne niż w postaci zwykłego tekstu.

W obu przypadkach tworzenie modelu prawie zawsze powoduje znaczny spadek niespójności i niejednoznaczności. Różne osoby zainteresowane działaniem mają często różne ustalenia świata firm, w którym działa system i różnych deweloperzy mają często różne ustalenia sposobu działania systemu. Przy użyciu modelu jako fokus dyskusję zazwyczaj udostępnia te różnice. Aby uzyskać więcej informacji o sposobie używania modelu zmniejszyć niespójności, zobacz [modelowanie wymagań użytkowników](../modeling/model-user-requirements.md).

## <a name="use-models-with-other-artifacts"></a>Używanie modeli za pomocą innych artefaktów

Model nie jest samodzielnie specyfikacji wymagania lub architektury. Jest to narzędzie dla wyraźniej wyrażania niektóre aspekty te rzeczy, ale nie wszystkie pojęcia, które są wymagane podczas projektowania oprogramowania, które mogą być wyrażone. Te modele w związku z tym powinien być używany razem z innych środków komunikacji, takimi jak program OneNote stron lub akapitów, dokumenty Microsoft Office, elementów roboczych w Team Foundation lub notatki na ścianie pokoju projektu. Niezależnie od ostatniego elementu wszystkie te typy obiektów mogą być połączone części elementów modelu.

Inne aspekty specyfikacji, które zazwyczaj są używane wraz z modeli, m.in. W zależności od skali i styl projektu mogą korzystać z kilku z tych aspektów lub używaj żadnego na wszystkich:

- Przypadki użycia. Scenariusz użycia jest krótki opis, oraz użytkowników i innych uczestników projektu jakiegoś aspektu zachowania systemu, które zostaną dostarczone w jednej iteracji projektu. Typowy scenariusz użycia, który rozpoczyna się "odbiorcy będą mogli..." Scenariusz użycia może powodować grupy przypadków użycia lub można zdefiniować rozszerzenia przypadki użycia, które zostały wcześniej opracowane. Definiowanie lub rozszerzanie przypadki użycia pomaga zwiększyć przejrzyste historii użytkownika.

- Żądania zmiany. Żądania zmiany w bardziej formalnych projektów jest bardzo podobny do scenariusza użycia w projekcie agile. Podejście agile co został opracowany w poprzedniej iteracji traktuje wszystkie wymagania zgodnie ze zmianami.

- Użyj przypadków opisu. Przypadek użycia reprezentuje jeden ze sposobów, w którym użytkownik korzysta z systemu w celu osiągnięcia określonego celu. Pełny opis zawiera cel, główne i alternatywnych sekwencji zdarzeń i wyjątkowe wyniki. Diagram przypadków użycia pomaga podsumowywania i omówiono jej przypadki użycia.

- Scenariusze. Scenariusz jest dość szczegółowy opis sekwencję zdarzeń, pokazujący, jak systemu, użytkowników i innych systemów współpracują ze sobą podania wartości do zainteresowanych stron. Może upłynąć postaci slide show interfejsu użytkownika lub prototypu interfejsu użytkownika. Można go opisać przypadek użycia jednego lub sekwencji przypadki użycia.

- Słownik. Słownik wymagania dotyczące projektu w tym artykule opisano słów, z którymi klienci omówić świata w. Modele wymagania i interfejsu użytkownika należy również użyć niniejsze postanowienia. Diagram klas może pomóc wyjaśnić relacje między większość tych terminów. Tworzenie diagramów i słownik nie tylko zmniejsza nieporozumień między użytkownikami i deweloperów, ale udostępnia również prawie zawsze nieporozumień między zainteresowane strony biznesowe różne.

- Reguły biznesowe. Może być wyrażona wiele reguł biznesowych, niezmienna ograniczenia dotyczące skojarzenia i atrybutów w modelu klasy wymagań, jak i ograniczenia na diagramach sekwencji.

- Projektowania wysokiego poziomu. W tym artykule opisano główne części i jak one współdziałają ze sobą. Składnik, sekwencji i diagramy interfejsu są główną częścią projektowania wysokiego poziomu.

- Wzorce projektowe. Opis reguły projektowania, które są współużytkowane w różnych częściach systemu.

- Przetestuj specyfikacji. Test skrypty i projekty kodu testu potrafi wykorzystać diagramów aktywności i sekwencji do opisania sekwencji kroków testu. Testy systemu muszą być wyrażone w modelu wymagań, dzięki czemu można łatwo można ich zmienić po zmianie wymagań.

- Plan projektu. Plan projektu lub zaległości definiuje dostarczenia każdej funkcji. Można zdefiniować każdej funkcji, co przypadków użycia i reguły biznesowe implementuje, lub rozszerzenie z informacją. Można albo odwołasz się do przypadków użycia i reguły biznesowe bezpośrednio w ramach planu, lub zdefiniować zestaw funkcji w oddzielny dokument i użyj tytuły funkcji w planie.

## <a name="use-models-in-iteration-planning"></a>Używanie modeli w ramach planowania iteracji

Mimo że wszystkie projekty różnią się w ich skalowania i organizacji, typowym projekcie jest planowana jako szereg iteracji między dwoma do sześciu tygodni. Jest to ważne, aby zaplanować wystarczająco dużo iteracji, aby umożliwić opinii od początku iteracji, które ma być używany do dostosowania zakresu i plany dotyczące późniejszej iteracji.

Poniższe sugestie może się okazać przydatne do osiągnięcia korzyści modelowania w projekcie iteracyjne.

### <a name="sharpen-focus-as-each-iteration-approaches"></a>Doskonalenie fokus, gdy zbliża się iteracja

Gdy zbliża się iteracja, aby uprościć określenie, co ma zostać dostarczona na końcu iteracji należy używać modeli.

- Nie modelu wszystko, co szczegółowo w wczesnych iteracjach. W pierwszej iteracji utworzenia diagramu klas głównych elementów w słowniku użytkownika narysować diagram przypadków użycia główne i narysować diagram główne składniki. Nie opisują któregoś z powyższych dokładniej przyjrzeć się ponieważ szczegóły zmieni się w dalszej części projektu. Umożliwia utworzenie listę funkcji lub główne przypadki użycia w warunkach określonych w tym modelu. Funkcje należy przypisać do iteracji, tak aby około równoważenia obciążenia szacowany w całym projekcie. Te przypisania zmieni się w dalszej części projektu.

- Spróbuj wdrożyć uproszczone wersje wszystkich najważniejszych przypadków użycia w wczesnych iteracji. Rozszerzenia te przypadki użycia w późniejszej iteracji. Takie podejście pomaga zmniejszyć ryzyko odnajdywania luka w wymaganiach lub architektury za późno w projekcie, aby podejmować żadnych działań na jego temat.

- Pod koniec każdej iteracji naciśnij i przytrzymaj workshop wymagania, aby zdefiniować szczegółowo, wymaganiami lub historią użytkowników, które będą rozwijane w następnej iteracji. Zaproś użytkowników i zainteresowane strony biznesowe, które można określić priorytety, a także deweloperom i testerom systemu. Zezwala na określenie wymagań dla iteracji 2-tygodniowych trzy godziny.

- Celem warsztatów jest wszystkim użytkownikom zgodę na to, co można zrobić przed zakończeniem następnej iteracji. Użyj modeli jako jedno z narzędzi, aby pomóc w wyjaśnianiu wymagania. Dane wyjściowe warsztatów to lista prac iteracji: oznacza to, listę zadań programistycznych w zestawach Team Foundation i testowania w [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)].

- W warsztacie wymagania omówiono w nim projekt pod warunkiem, że należy określić szacunki dla zadania programistyczne. W przeciwnym razie Zachowaj dyskusji zachowania systemu, który użytkownicy będą mogli doświadczyć bezpośrednio. Zachowaj modelu wymagań niezależnie od architektury model.

- Nietechnicznym zainteresowane strony mają zwykle informacji o żadnych problemach zrozumienie diagramy UML, za pomocą wskazówki od Ciebie.

### <a name="link-model-to-work-items"></a>Model łączy do elementów roboczych

Po warsztaty wymagania opracowania szczegółowe informacje o modelu wymagań, a następnie połącz modelu zadań programistycznych. Można to zrobić, łącząc elementy robocze w Team Foundation do elementów w modelu.

Można połączyć dowolny element do elementów roboczych, ale najbardziej przydatne elementy są następujące:

- Komentarz opisujący reguł biznesowych lub jakość wymagań usługi. Aby uzyskać więcej informacji, zobacz [modelowanie wymagań użytkowników](../modeling/model-user-requirements.md).

### <a name="link-model-to-tests"></a>Model łącze do testów

Przewodnik dotyczący projektowania testów akceptacyjnych przy użyciu modelu wymagań. Utwórz testy wątkom prace deweloperskie.

Aby dowiedzieć się więcej na temat tej techniki, zobacz [opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md).

### <a name="estimate-remaining-work"></a>Oszacowanie pracy pozostałej

Modelu wymagań może pomóc oszacowanie całkowitego rozmiaru projektu w odniesieniu do rozmiaru każdej iteracji. Ocena liczba i złożoność przypadków użycia i klas może ułatwić oszacowanie prac projektowych, które będzie wymagane. Po wykonaniu kilku pierwszych iteracjach, porównanie wymagania objętych usługą i wymagania nadal na pokrycie można nadać przybliżony miara kosztu i zakresu w pozostałej części projektu.

Pod koniec każdej iteracji Przejrzyj przypisanie wymogów do przyszłych iteracji. Może być przydatna do reprezentowania stanu oprogramowania na końcu każdej iteracji jak podsystemu na diagramie przypadków użycia. Twoje dyskusje możesz przenieść przypadki użycia i korzystanie z rozszerzeń przypadków z jednego z tych podsystemów, do innego.

## <a name="levels-of-abstraction"></a>Poziomy abstrakcji

Modele mają zakres abstrakcji w odniesieniu do oprogramowania. Najbardziej konkretnych modele reprezentują bezpośrednio kodu programu i najbardziej abstrakcyjne modele reprezentują koncepcji biznesowych, którzy mogą lub nie może być reprezentowany w kodzie.

Model można wyświetlić za pomocą kilka rodzajów diagramów. Aby uzyskać informacji na temat modeli i diagramów, zobacz [tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md).

Różne rodzaje diagramów są przydatne do opisywania projektu na różnych poziomach abstrakcji. Wiele typów diagram przydają się w więcej niż jeden poziom. W poniższej tabeli przedstawiono, jak używać każdego typu diagramu.

|Poziom projektu|Typy diagramów|
|-|-|
|Proces biznesowy<br /><br /> Rozpoznając kontekst, w którym będzie używany system pomaga zrozumieć, jakie użytkownicy z niego.|— Diagramy klas koncepcyjny opisują koncepcji biznesowych używanych w ramach procesu biznesowego.|
|Wymagania dotyczące użytkownika<br /><br /> Definicja użytkownicy muszą z systemu.|— Reguły biznesowe i jakość wymagań usługi można opisać w oddzielnych dokumentów.|
|Wysoki poziom projektu<br /><br /> Ogólną strukturę systemu: główne składniki i sposób ich połączyć ze sobą.|— Diagramów zależności opis struktury systemu na współzależne części. Można sprawdzić poprawność kodu programu względem diagramów zależności, aby upewnić się, że są zgodne z architekturą.|
|Analiza kodu<br /><br /> Diagramy można wygenerować z kodu.|— Diagramy zależności Pokaż zależności między klasami. Zaktualizowany kod może być sprawdzana diagram zależności.<br />— Diagramy klas Pokaż klasy w kodzie.|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategoria**|**Łącza**|
|-|-|
|**Filmy wideo**|![Link do klipu wideo](../data-tools/media/playvideo.gif) [MSDN jak mogę wideo: Sposób tworzenia i używania modeli UML i diagramów (Visual Studio 2010 w wersji Ultimate)](http://go.microsoft.com/fwlink/?LinkId=214460)<br /><br /> ![Link do klipu wideo](../data-tools/media/playvideo.gif) [witryny Channel 9: UML w programie Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkID=201106)<br /><br /> ![Link do klipu wideo](../data-tools/media/playvideo.gif) [MSDN jak mogę serii: Narzędzia UML i rozszerzalność (Visual Studio 2010 w wersji Ultimate)](http://go.microsoft.com/fwlink/?LinkID=214467)|
|**Fora**|- [Program Visual Studio visualization and Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />- [Program Visual Studio visualization and Modeling SDK (narzędzia DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blogi**|[Microsoft DevOps](https://devblogs.microsoft.com/devops/)|
|**Artykuły techniczne i dzienniki**|[Centrum MSDN architektury](http://go.microsoft.com/fwlink/?LinkId=201343)<br /><br /> [Architektura Visual Studio — wskazówki dotyczące oprzyrządowania](../modeling/visual-studio-architecture-tooling-guidance.md)|

## <a name="see-also"></a>Zobacz także

- [Używaj modeli w Agile development](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)
- [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)
- [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)
- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)
- [Opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md)
- [Tworzenie struktury rozwiązania modelowania](../modeling/structure-your-modeling-solution.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
