---
title: Wytyczne od społeczności deweloperów
description: W tym artykule opisano wytyczne dotyczące pracy z Visual Studio Developer Community.
ms.date: 6/30/2020
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 21cf3bd6a0c208a78cd391f93702865e905482e0
ms.sourcegitcommit: 3c6c263a1c0b20f084290ce45295a46027da33b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2021
ms.locfileid: "113756890"
---
# <a name="developer-community-guidelines"></a>Wytyczne od społeczności deweloperów

Centrum deweloperów Community śledzi problemy i sugestie dotyczące funkcji Visual Studio.

## <a name="submitting-problems-and-suggestions"></a>Przesyłanie problemów i sugestii

W [Visual Studio Developer Community](https://aka.ms/feedback/suggest?space=8) śledzi problemy i sugestie dotyczące funkcji dla Visual Studio.

### <a name="before-submitting-an-issue"></a>Przed przesłaniem problemu

Wyszukaj swój problem na stronie Visual Studio Developer Community, aby upewnić się, że jeszcze nie istnieje. Jeśli znajdziesz problem, który już istnieje, zamieć odpowiednie komentarze i zagłosuj.

Jeśli problem jest pytaniem, zadaj pytanie społeczności na Stack Overflow [przy](https://stackoverflow.com/questions/tagged/visual-studio?tab=Newest) użyciu tagu _visual-studio_. Mamy personel działu pomocy technicznej, który monitoruje ten tag, i pomoże nam odpowiedzieć na pytania.

Jeśli nie możesz znaleźć istniejącego problemu, który opisuje Twoją usterkę lub funkcję, prześlij problem, korzystając z poniższych wskazówek.

### <a name="writing-a-good-bug-report-or-feature-suggestion"></a>Pisanie dobrego raportu o usterce lub sugestii dotyczącej funkcji

- Dla każdego problemu należy zwrócić tylko jedno żądanie problemu lub funkcji.

  - Połączenie wielu problemów lub żądań funkcji w jeden problem utrudnia nam diagnozowanie i utrudnia innym użytkownikom głosowanie na twój problem.
  - Nie należy dodawać problemu jako komentarza do istniejącego problemu, chyba że dotyczy on identycznych danych wejściowych. Wiele problemów wygląda podobnie, ale ma różne przyczyny, co utrudnia nam diagnozowanie problemu.

- Im więcej informacji możesz podać, tym łatwiej będzie nam odtworzyć i rozwiązać problem.
- Uwzględnij następujące kroki dla każdego problemu.

  - Powtarzalne kroki (1... 2... 3...) i oczekiwanych danych w porównaniu z tym, czego doświadczyliśmy.
  - Obrazy, animacje lub link do wideo. Obrazy i animacje ilustrują kroki ponownego tworzenia, _ale nie zastępują_ ich.
  - W razie potrzeby fragment kodu, który demonstruje problem, lub link do repozytorium kodu, można łatwo ściągnąć na naszą maszynę, aby ponownie utworzyć problem.

- Pamiętaj, aby wykonać następujące czynności:

  - Wyszukaj, aby sprawdzić, czy istnieje duplikat. Jeśli tak, zagłosuj na istniejący problem, podając dodatkowe komentarze lub wyjaśnienia zgodnie z potrzebami.
  - Po wyłączeniu wszystkich rozszerzeń utwórz ponownie problem. Jeśli znajdziesz, że problem jest spowodowany przez zainstalowane rozszerzenie, odpowiednio w pliku problemu.
  - Uprość kod wokół problemu, abyśmy lepiej go wyizolować.

Nawet w przypadku problemów, które zawierają szczegółowe informacje, być może nie możemy odtworzyć problemu i możemy poprosić o więcej informacji.

## <a name="managing-problem-reports"></a>Zarządzanie raportami problemów

Triaging an issue is a multi-step process that is collaboratively done within the feature team. Zazwyczaj trwa to tydzień, ale może trwać dłużej. Celem trygorowania jest zapewnienie jasnego zrozumienia, co się stanie z problemem. Na przykład po zakończeniu oceny wiesz, czy planujemy rozwiązanie problemu, czy zaczekasz na więcej opinii społeczności.

Po zgłoszeniu problemu stany wskazują, gdzie twoje zgłoszenia znajdują się w ich cyklu życia. Gdy Visual Studio produktu przejrzyją Twoją opinię, ustawią ją z odpowiednim stanem. Śledź postęp raportów o problemach, odwołując się do stanów [problemów i często zadawanych pytań.](./report-a-problem.yml)

### <a name="prioritizing-which-issues-to-fix"></a>Określanie priorytetów problemów do rozwiązania

Nie możemy rozwiązać wszystkich zgłoszonych problemów. Niektóre z nich są zbyt kosztowne do naprawienia, inne mogą się pogonić w innych obszarach funkcji, a niektóre mogą mieć zbyt mały wpływ. Rozumiemy, że może to być przytłaczające, jeśli masz czas na wysłanie do nas raportu o problemie. Wszyscy tu jesteśmy, niezależnie od tego, czy w tym projekcie, czy innych, które współtwomentowaliśmy. Jeśli problem został zamknięty i uważasz, że przyczyna nie jest satysfakcjonujące, możesz wyjaśnić swój przypadek użycia i zażądać ponownego aktywowania problemu dla innego przebiegu. W tym momencie możemy cię poprosić o dodatkowe informacje.

### <a name="missing-important-information"></a>Brak ważnych informacji

Jeśli brakuje ważnych informacji, przypisujemy stan _Wymaga dodatkowych_ informacji. Skomentuj problem z konkretnymi potrzebnymi informacjami, a otrzymasz powiadomienie e-mail. Jeśli nie otrzymamy tych informacji w ciągu siedmiu dni, wyślemy Ci przypomnienie. Następnie zamykamy bilet po upływie 14 dni braku aktywności.

### <a name="other-product"></a>Inny produkt

Czasami podczas zgłaszania problemu okazuje się, że przyczyną jest inny produkt, a nie Visual Studio. Może to być inna powiązana aplikacja lub rozszerzenie. 

W takim przypadku zamkniemy problem i poprosimy Cię o otwarcie go z innym produktem. Poniżej podano kilka typowych miejsc, w których można je rozwiązać:

* [SQL Server](https://feedback.azure.com/forums/908035-sql-server)
* [Visual Studio Obsługa subskrypcji](https://feedback.azure.com/forums/908035-sql-server)
* [Office](https://support.office.com/article/how-do-i-give-feedback-on-microsoft-office-2b102d44-b43f-4dd2-9ff4-23cf144cfb11)
* [Windows](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)

#### <a name="additional-information"></a>Dodatkowe informacje

- [Jak zwiększyć szanse na naprawienie problemu z wydajnością](./how-to-increase-chances-of-performance-issue-being-fixed.md)
- [Rozwiązywanie problemów i tworzenie dzienników MSBuild problemów](./msbuild-logs.md)

## <a name="managing-feature-suggestions"></a>Zarządzanie sugestiami funkcji

Sugestie dotyczące funkcji to sposób komunikacji między nami i członkami społeczności deweloperów. Technicznie rzecz ujmujemy, że wszystkie żądania funkcji mogą być otwarte na zawsze. Jednak utrzymywanie otwartych problemów zmniejszy wgląd społeczności w rzeczywisty stan funkcji. Dlatego zamykamy żądania funkcji, które nie będą adresowane i nie przypiszemy funkcji, które możemy rozwiązać, do _etykiety Under Review_ (Pod recenzją).

Jeśli zasugerowano funkcję, być może nie planujemy rozsyłać Twojego żądania. Rozumiemy to. Wszyscy jesteśmy tam — w tym projekcie lub innych osobach, które współtwomentowaliśmy. Dlatego cieszymy się, że pokochamy wszystkie Twoje dane wejściowe. Nie wywłaszaj osobistych nagorów, gdy zamkniemy lub przypiszemy _etykietę Under Review_ do Twojej sugestii. Jeśli uważasz, że twoja sugestia funkcji jest otwarta, wyjaśnij swój przypadek użycia i skontaktuj się z nami lub zbierz więcej głosów.

W naszym procesie podejmowania decyzji przyjrzymy się następującym charakterystykom sugestii funkcji:

- Czy jest to zgodne z naszym ogólnym kierunkiem produktu?
- Czy możemy sobie pozwolić na jego skompilowanie i utrzymanie?
- Czy jest to zgodne z naszą ogólną [strategią harmonogramu](/visualstudio/productinfo/vs-roadmap) działania?
- Czy jest ona wspierana przez społeczność, na co wskazują głosy i komentarze?
- Czy lubimy to, nawet w przypadku niskiej pomocy społeczności?

Jeśli nie możemy odpowiedzieć "tak" na dowolne z tych pytań, zamkniemy je. Jednak często sugestia pozostanie otwarta jako _W trakcie przeglądu,_ aby zebrać więcej opinii społeczności.

Jeśli sugestia nie pasuje do ogólnego kierunku produktu, zamkniemy ją jako *poza zakresem*. Na przykład możemy mieć podobne inwestycje w innych członków Visual Studio rodziny produktów. Lub sugerowana funkcja może być odpowiednia tylko dla kilku osób, przez co rozszerzenie lepiej nadaje się do jego zapewnienia.

Śledź postęp sugestii dotyczącej funkcji, odwołując się do stanów [sugestii i często zadawanych pytań.](./report-a-problem.yml)

## <a name="discussion-etiquette"></a>Omówienie

Aby zapewnić czytelność i przejrzystość konwersacji, ogranicz dyskusję do języka angielskiego i zachowaj znaczenie dla problemu. Należy uważać na innych i zawsze starać się być uprzejme i profesjonalne.

Aby uzyskać więcej informacji, zobacz Microsoft Community Code of Conduct ( Kodeks [postępowania firmy Microsoft).](https://answers.microsoft.com/en-us/page/codeofconduct)

Wszelkie naruszenia zasad dyskusji mogą prowadzić do usunięcia komentarza i ewentualnego zablokowania użytkownika.

## <a name="data-privacy"></a>Prywatność danych

Komentarze i odpowiedzi są publicznie widoczne, ale wszystkie dołączone pliki są prywatnie udostępniane tylko firmie Microsoft. Ta widoczność jest korzystna, ponieważ umożliwia całej społeczności zobaczenie problemów i rozwiązań znalezionych przez innych użytkowników. Jeśli martwisz się prywatnością danych lub tożsamości, masz do wyboru opcje. Przeczytaj więcej na [temat prywatności Community dewelopera.](./developer-community-privacy.md)

## <a name="next-steps"></a>Następne kroki

Przejdź do witryny Visual Studio [Developer Community](https://aka.ms/feedback/suggest?space=8) zgłaszania problemów, sugerowania funkcji lub przeglądania istniejących biletów. Owocnej pracy.
