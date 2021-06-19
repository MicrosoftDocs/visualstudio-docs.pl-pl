---
title: Używanie modeli w procesie tworzenia aplikacji
description: Dowiedz się, Visual Studio, możesz użyć modelu, aby ułatwić zrozumienie i zmianę systemu, aplikacji lub składnika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, using models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 095a6f17691d3265320a7b77905f70903bec1cb5
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388506"
---
# <a name="use-models-in-your-development-process"></a>Używanie modeli w procesie tworzenia aplikacji

W Visual Studio można użyć modelu, aby ułatwić zrozumienie i zmianę systemu, aplikacji lub składnika. Model może pomóc w wizualizacji świata, w którym działa system, wyjaśnieniu potrzeb użytkowników, zdefiniowaniu architektury systemu, przeanalizowaniu kodu i upewnieniu się, że kod spełnia wymagania. Zobacz [wideo z kanału Channel 9: Ulepszanie architektury za pomocą modelowania](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling).

Aby sprawdzić, które wersje Visual Studio obsługują poszczególne typy modelu, zobacz Obsługa wersji dla architektury [i narzędzi do modelowania.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

Modele mogą pomóc na kilka sposobów:

- Rysowanie diagramów modelowania ułatwia wyjaśnienie pojęć związanych z wymaganiami, architekturą i projektem wysokiego poziomu. Aby uzyskać więcej informacji, zobacz [Model user requirements (Wymagania użytkownika modelu).](../modeling/model-user-requirements.md)

- Praca z modelami może pomóc uwidocznić niespójności w wymaganiach.

- Komunikacja z modelami ułatwia mniej niejednoznaczne komunikowanie ważnych koncepcji niż w języku naturalnym. Aby uzyskać więcej informacji, zobacz [Model your app's architecture (Modelowanie architektury aplikacji).](../modeling/model-your-app-s-architecture.md)

- Czasami można używać modeli do generowania kodu lub innych artefaktów, takich jak schematy bazy danych lub dokumenty. Na przykład składniki modelowania Visual Studio są generowane na podstawie modelu. Aby uzyskać więcej informacji, zobacz [Generowanie i konfigurowanie aplikacji na podstawie modeli.](../modeling/generate-and-configure-your-app-from-models.md)

Modeli można używać w wielu różnych procesach, od niezwykle elastycznych po wysokie procedury.

## <a name="use-models-to-reduce-ambiguity"></a>Używanie modeli w celu zmniejszenia niejednoznaczności

Język modelowania jest mniej niejednoznaczny niż język naturalny i jest przeznaczony do wyrażania koncepcji zwykle wymaganych podczas tworzenia oprogramowania.

Jeśli Twój projekt ma mały zespół, który korzysta z rozwiązań zwinnych, możesz użyć modeli, aby ułatwić wyjaśnienie historii użytkownika. W dyskusjach z klientem na temat ich potrzeb utworzenie modelu może wygenerować przydatne pytania znacznie szybciej i w szerszym obszarze produktu, niż pisanie skoku lub prototypu kodu.

Jeśli projekt jest duży i obejmuje zespoły z różnych części świata, możesz użyć modeli, aby znacznie efektywniej komunikować wymagania i architekturę niż w przypadku zwykłego tekstu.

W obu przypadkach utworzenie modelu prawie zawsze skutkuje znacznym zmniejszeniem niespójności i niejednoznaczności. Różni uczestnicy projektu często rozumieją świat biznesowy, w którym działa system, a różni deweloperzy często mają różne informacje na temat sposobu działania systemu. Używanie modelu jako fokusu dyskusji zwykle ujawnia te różnice. Aby uzyskać więcej informacji na temat sposobu używania modelu w celu zmniejszenia [niespójności,](../modeling/model-user-requirements.md)zobacz Wymagania użytkownika modelu .

## <a name="use-models-with-other-artifacts"></a>Używanie modeli z innymi artefaktami

Model sam w sobie nie jest specyfikacją wymagań ani architekturą. Jest to narzędzie do bardziej jasnego wyrażania niektórych aspektów tych rzeczy, ale nie wszystkie koncepcje wymagane podczas projektowania oprogramowania można wyrazić. W związku z tym modele powinny być używane razem z innymi środkami komunikacji, takimi jak strony lub akapity programu OneNote, dokumenty Microsoft Office, elementy robocze w programie Team Foundation lub karteczki na tablicy projektowej. Oprócz ostatniego elementu wszystkie te typy obiektów można połączyć z elementami części modelu.

Poniżej przedstawiono inne aspekty specyfikacji, które są zwykle używane razem z modelami. W zależności od skali i stylu projektu możesz użyć kilku z tych aspektów lub w ogóle ich nie używać:

- Historie użytkownika. Historia użytkownika to krótki opis, omówiony z użytkownikami i innymi uczestnikami projektu, aspekt zachowania systemu, który zostanie dostarczony w jednej z iteracji projektu. Typowy scenariusz użytkownika zaczyna się od "Klient będzie mógł...". Historia użytkownika może wprowadzać grupę przypadków użycia lub może definiować rozszerzenia przypadków użycia, które zostały wcześniej opracowane. Definiowanie lub rozszerzanie przypadków użycia pomaga w bardziej czytelnym cytująco.

- Żądania zmiany. Żądanie zmiany w bardziej formalnym projekcie jest bardzo podobne do historii użytkownika w projekcie Agile. Podejście agile traktuje wszystkie wymagania jako zmiany w tym, co zostało opracowane w poprzednich iteracjach.

- Opis przypadku użycia. Przypadek użycia reprezentuje jeden ze sposobów interakcji użytkownika z systemem w celu osiągnięcia określonego celu. Pełny opis zawiera cel, główne i alternatywne sekwencje zdarzeń oraz wyjątkowe wyniki. Diagram przypadków użycia ułatwia podsumowanie i omówienie przypadków użycia.

- Scenariuszy. Scenariusz to dość szczegółowy opis sekwencji zdarzeń pokazujących, jak system, użytkownicy i inne systemy współpracują ze sobą, aby zapewnić wartość uczestnikom projektu. Może to mieć formę pokazu slajdów interfejsu użytkownika lub prototypu interfejsu użytkownika. Może opisywać jeden przypadek użycia lub sekwencję przypadków użycia.

- Słownik entry. W słowniku wymagań projektu opisano słowa, z którymi klienci omawiają swój świat. W modelach interfejsu użytkownika i wymagań należy również używać tych terminów. Diagram klas może pomóc w wyjaśnieniu relacji między większość z tych terminów. Tworzenie diagramów i słownika nie tylko zmniejsza liczbę nieporozumień między użytkownikami i deweloperami, ale prawie zawsze ujawnia nieporozumienia między różnymi uczestnikami projektu biznesowego.

- Reguły biznesowe. Wiele reguł biznesowych można wyrazić jako niezmienne ograniczenia skojarzeń i atrybutów w modelu klas wymagań oraz jako ograniczenia na diagramach sekwencji.

- Projekt wysokiego poziomu. Opisuje główne części i sposób ich dopasowania. Diagramy składników, sekwencji i interfejsu są główną częścią projektu wysokiego poziomu.

- Wzorce projektowe. Opis reguł projektowania, które są współużytkujące w różnych częściach systemu.

- Specyfikacje testów. Skrypty testowe i projekty kodu testowego mogą dobrze wykorzystywać diagramy działań i sekwencji do opisywania sekwencji kroków testu. Testy systemowe powinny być wyrażane jako model wymagań, aby można je było łatwo zmienić po zmianie wymagań.

- Plan projektu. Plan projektu lub zaległości określają, kiedy poszczególne funkcje zostaną dostarczone. Każdą funkcję można zdefiniować, podając przypadki użycia i reguły biznesowe, które implementuje lub rozszerza. Można odwoływać się do przypadków użycia i reguł biznesowych bezpośrednio w planie lub zdefiniować zestaw funkcji w oddzielnym dokumencie i używać tytułów funkcji w planie.

## <a name="use-models-in-iteration-planning"></a>Używanie modeli w planowaniu iteracji

Mimo że wszystkie projekty różnią się pod swoją skalą i organizacją, typowy projekt jest zaplanowany jako seria iteracji z zakresie od dwóch do sześciu tygodni. Ważne jest, aby zaplanować wystarczającą ilość iteracji, aby umożliwić informacje zwrotne z wczesnych iteracji, aby można było dostosować zakres i plany dla późniejszych iteracji.

Poniższe sugestie mogą pomóc w zrealizowaniu korzyści wynikających z modelowania w projekcie iteracyjnym.

### <a name="sharpen-focus-as-each-iteration-approaches"></a>Skupienie fokusu podczas każdej iteracji

Podczas podejścia do każdej iteracji należy używać modeli, aby ułatwić zdefiniowanie, co ma zostać dostarczone na końcu iteracji.

- Nie modeluj wszystkiego szczegółowo we wczesnych iteracjach. W pierwszej iteracji utwórz diagram klas dla głównych elementów w słowniku użytkownika, narysuj diagram głównych przypadków użycia i narysuj diagram głównych składników. Nie należy szczegółowo opisywać żadnego z tych informacji, ponieważ szczegóły ujdą w dalszej części projektu. Użyj terminów zdefiniowanych w tym modelu, aby utworzyć listę funkcji lub głównych historii użytkownika. Przypisz funkcje do iteracji, aby w przybliżeniu zrównoważyć szacowane obciążenie w całym projekcie. Te przypisania zmienią się w dalszej części projektu.

- Spróbuj zaimplementować uproszczone wersje wszystkich najważniejszych przypadków użycia we wczesnej iteracji. Rozszerz te przypadki użycia w późniejszych iteracjach. Takie podejście pomaga zmniejszyć ryzyko wystąpienia wady wymagań lub zbyt późnego opóźnienia architektury w projekcie, aby coś z tym zrobić.

- Pod koniec każdej iteracji należy zorganizować warsztaty dotyczące wymagań w celu szczegółowego zdefiniowania wymagań lub historii użytkownika, które zostaną opracowane w następnej iteracji. Zaproś użytkowników i uczestników projektu, którzy mogą decydować o priorytetach, a także deweloperów i testerów systemu. Pozwól trzy godziny na zdefiniowanie wymagań dla iteracji 2-tygodniowej.

- Celem warsztatów jest, aby wszyscy uzgodnili, co zostanie osiągnąć do końca następnej iteracji. Użyj modeli jako jednego z narzędzi, aby ułatwić wyjaśnienie wymagań. Dane wyjściowe warsztatów to lista prac iteracji, czyli lista zadań programistyki w programie Team Foundation i w próchniach testów w programie [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] .

- W warsztatach dotyczących wymagań omów projekt, który jest tylko niesłabnący, ponieważ musisz określić oszacowania dla zadań programistów. W przeciwnym razie należy zachować dyskusję na temat zachowania systemu, które użytkownicy mogą bezpośrednio doświadczyć. Model wymagań należy oddzielić od modelu architektonicznego.

- Nietechniczne osoby zainteresowane zazwyczaj nie mają problemów ze zrozumieniem diagramów UML, z pewnymi wskazówkami od Ciebie.

### <a name="link-model-to-work-items"></a>Łączenie modelu z elementami pracy

Po warsztatach dotyczących wymagań szczegółowo opracuj model wymagań i połącz go z zadaniami programistyki. Można to zrobić, łącząc elementy robocze w programie Team Foundation z elementami w modelu.

Można połączyć dowolny element z elementami pracy, ale najbardziej przydatne elementy są następujące:

- Komentarze opisujące reguły biznesowe lub wymagania dotyczące jakości usług. Aby uzyskać więcej informacji, zobacz [Model user requirements (Wymagania użytkownika modelu).](../modeling/model-user-requirements.md)

### <a name="link-model-to-tests"></a>Łączenie modelu z testami

Użyj modelu wymagań, aby kierować projektowaniem testów akceptacyjnych. Te testy można tworzyć współbieżnie z pracami programistyki.

Aby dowiedzieć się więcej na temat tej techniki, zobacz [Develop tests from a model (Opracowywanie testów z modelu).](../modeling/develop-tests-from-a-model.md)

### <a name="estimate-remaining-work"></a>Szacowanie pozostałej pracy

Model wymagań może pomóc oszacować całkowity rozmiar projektu w odniesieniu do rozmiaru każdej iteracji. Ocena liczby i złożoności przypadków użycia i klas może pomóc oszacować wymagane prace programowe. Po ukończeniu kilku pierwszych iteracji porównanie objętych wymagań i wymagań, które nadal należy spełnić, może zapewnić przybliżoną miarę kosztu i zakresu pozostałej części projektu.

Pod koniec każdej iteracji przejrzyj przypisywanie wymagań do przyszłych iteracji. Może być przydatne do reprezentowania stanu oprogramowania na końcu każdej iteracji jako podsystemu w diagramie przypadków użycia. W dyskusjach można przenosić przypadki użycia i rozszerzenia przypadków użycia z jednego z tych podsystemów do innego.

## <a name="levels-of-abstraction"></a>Poziomy abstrakcji

Modele mają szereg abstrakcji w odniesieniu do oprogramowania. Najbardziej konkretne modele bezpośrednio reprezentują kod programu, a najbardziej abstrakcyjne modele reprezentują koncepcje biznesowe, które mogą lub nie być reprezentowane w kodzie.

Model można wyświetlić za pomocą kilku rodzajów diagramów. Aby uzyskać informacje o modelach i diagramach, zobacz Create models for your app (Tworzenie [modeli dla aplikacji).](../modeling/create-models-for-your-app.md)

Różne rodzaje diagramów są przydatne do opisywania projektu na różnych poziomach abstrakcji. Wiele typów diagramów jest przydatnych na więcej niż jednym poziomie. W tej tabeli pokazano, jak można używać poszczególnych typów diagramów.

|Poziom projektowania|Typy diagramów|
|-|-|
|Proces biznesowy<br /><br /> Zrozumienie kontekstu, w którym będzie używany system, pomaga zrozumieć, czego potrzebują użytkownicy.|— Diagramy klas koncepcyjnych opisują koncepcje biznesowe używane w procesie biznesowym.|
|Wymagania użytkownika<br /><br /> Definicja potrzeb użytkowników w systemie.|— Reguły biznesowe i wymagania dotyczące jakości usług można opisać w oddzielnych dokumentach.|
|Projekt wysokiego poziomu<br /><br /> Ogólna struktura systemu: główne składniki i sposób ich parowania.|— Diagramy zależności opisują strukturę systemu w zależności od siebie. Możesz zweryfikować kod programu względem diagramów zależności, aby upewnić się, że jest on zgodny z architekturą.|
|Analiza kodu<br /><br /> Na podstawie kodu można generować diagramy.|- Diagramy zależności pokazują zależności między klasami. Zaktualizowany kod można zweryfikować na diagramie zależności.<br />- Diagramy klas pokazują klasy w kodzie.|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategoria**|**Linki**|
|-|-|
|**Filmy wideo**|![link do wideo ](../data-tools/media/playvideo.gif) [MSDN How Do I Videos: How to Create and Use UML Models and Diagrams (Jak tworzyć modele i diagramy UML i używać ich w witrynie MSDN: how to Create and Use UML Models and Diagrams) (Visual Studio 2010 Ultimate)](/previous-versions/visualstudio/visual-studio-2010/dd831853(v=vs.100))<br /><br /> ![link do filmu ](../data-tools/media/playvideo.gif) [wideo Channel 9: UML with Visual Studio 2010](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-1-brainstorming-a-project)<br /><br /> ![link do wideo ](../data-tools/media/playvideo.gif) [MSDN How Do I Series: UML Tools and Extensibility (Visual Studio 2010 Ultimate)](/previous-versions/visualstudio/visual-studio-2010/dd831853(v=vs.100))|
|**Fora**|- [Visual Studio Visualization & Modeling Tools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio Visualization & Modeling SDK (narzędzia DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogi**|[Microsoft DevOps](https://devblogs.microsoft.com/devops/)|
|**Artykuły techniczne i dzienniki**|[Centrum architektury MSDN](/previous-versions/dn630665(v=msdn.10))|

## <a name="see-also"></a>Zobacz też

- [Używanie modeli w programie Agile Development](/previous-versions/ff398061(v=vs.140))
- [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)
- [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)
- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)
- [Opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md)
- [Tworzenie struktury rozwiązania modelowania](../modeling/structure-your-modeling-solution.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]