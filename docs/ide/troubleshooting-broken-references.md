---
title: Rozwiązywanie problemów z przerwanymi odwołaniami
ms.date: 03/21/2017
ms.topic: troubleshooting
helpviewer_keywords:
- C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c5efe0d5ba8d00f7bfc362dd702f45dfa627c20
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647386"
---
# <a name="troubleshoot-broken-references"></a>Rozwiązywanie problemów z przerwanymi odwołaniami

Jeśli aplikacja próbuje użyć uszkodzonego odwołania, zostanie wygenerowany błąd wyjątku. Brak możliwości znalezienia składnika, do którego się odwoływano, jest podstawowym wyzwalaczem błędu, ale istnieje kilka sytuacji, w których odwołanie może być uważane za zerwane. Te wystąpienia przedstawiono na poniższej liście:

- Ścieżka odwołania projektu jest nieprawidłowa lub niekompletna.

- Plik, do którego się odwoływano, został usunięty.

- Nazwa pliku, do którego występuje odwołanie, została zmieniona.

- Nie można nawiązać połączenia sieciowego lub uwierzytelniania.

- Odwołanie dotyczy składnika COM, który nie jest zainstalowany na komputerze.

Poniżej wymieniono te problemy.

> [!NOTE]
> Do plików w zestawach są przywoływane ścieżki bezwzględne w pliku projektu. W związku z tym użytkownicy, którzy pracują w środowisku wielorozwijania, nie mają zestawu, do którego odwołuje się w środowisku lokalnym. Aby uniknąć tych błędów, w takich przypadkach lepiej jest dodać odwołania projektu do projektu. Aby uzyskać więcej informacji, zobacz [programowanie z zestawami](/dotnet/framework/app-domains/programming-with-assemblies).

## <a name="reference-path-is-incorrect"></a>Ścieżka odwołania jest niepoprawna

Jeśli projekty są udostępniane na różnych komputerach, niektóre odwołania mogą nie zostać znalezione, gdy składnik znajduje się w innym katalogu na każdym komputerze. Odwołania są przechowywane pod nazwą pliku składnika (na przykład *komponentem webcomponent*). Po dodaniu odwołania do projektu, lokalizacja folderu pliku składnika (na przykład *C:\MyComponents*) jest dołączana do właściwości projektu **ReferencePath** .

Gdy projekt zostanie otwarty, próbuje zlokalizować te pliki, do których się odwołuje, przeglądając katalogi na ścieżce odwołania. Jeśli projekt zostanie otwarty na komputerze, który przechowuje składnik w innym katalogu, na przykład *D:\MyComponents*, nie można odnaleźć odwołania i pojawi się błąd w **Lista zadań**.

Aby rozwiązać ten problem, można usunąć uszkodzone odwołanie, a następnie zastąpić je za pomocą okna dialogowego **Dodaj odwołanie** . Innym rozwiązaniem jest użycie elementu **Path Reference** na stronach właściwości projektu i zmodyfikowanie folderów na liście, aby wskazywały poprawne lokalizacje. Właściwość **Path Reference** jest utrwalona dla każdego użytkownika na każdym komputerze. W związku z tym modyfikacja ścieżki odniesienia nie ma wpływu na innych użytkowników projektu.

> [!TIP]
> Odwołania projektu do projektu nie mają tych problemów. Z tego powodu należy używać ich zamiast odwołań do plików, jeśli jest to możliwe.

### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Aby naprawić uszkodzone odwołanie do projektu poprzez poprawienie ścieżki odwołania

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu, a następnie kliknij polecenie **Właściwości**.

   Zostanie wyświetlony **Projektant projektu** .

1. Jeśli używasz Visual Basic, wybierz stronę **odwołania** , a następnie kliknij przycisk **ścieżki odwołania** . W oknie dialogowym **ścieżki odwołań** wpisz ścieżkę do folderu zawierającego element, do którego chcesz się odwołać w polu **folder** , a następnie kliknij przycisk **Dodaj folder** .

    Jeśli używasz programu C#, wybierz stronę **ścieżki odwołania** . W polu **folder** wpisz ścieżkę do folderu, który zawiera element, którego chcesz użyć, a następnie kliknij przycisk **Dodaj folder** .

## <a name="referenced-file-has-been-deleted"></a>Plik, do którego istnieje odwołanie, został usunięty

Istnieje możliwość, że plik, do którego się odwołuje, został usunięty i nie znajduje się już na dysku.

### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Aby naprawić uszkodzone odwołanie do projektu dla pliku, który już nie istnieje na dysku

- Usuń odwołanie.

- Jeśli odwołanie istnieje w innej lokalizacji na komputerze, przeczytaj ją z tej lokalizacji.

## <a name="referenced-file-has-been-renamed"></a>Nazwa pliku, do którego istnieje odwołanie

Istnieje możliwość, że nazwa pliku, do którego istnieje odwołanie.

### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Aby naprawić uszkodzone odwołanie dla pliku, którego nazwa została zmieniona

- Usuń odwołanie, a następnie Dodaj odwołanie do pliku o zmienionej nazwie.

- Jeśli odwołanie istnieje w innej lokalizacji na komputerze, należy je odczytać z tej lokalizacji.

## <a name="network-connection-or-authentication-has-failed"></a>Połączenie sieciowe lub uwierzytelnianie nie powiodło się

Może istnieć wiele możliwych przyczyn dla niedostępnych plików: nieudane połączenie sieciowe lub nieudane uwierzytelnienie. Każda Przyczyna może mieć unikatowy sposób odzyskiwania. na przykład może być konieczne skontaktowanie się z administratorem lokalnym w celu uzyskania dostępu do wymaganych zasobów. Jednak usunięcie odwołania i naprawienie użytego kodu jest zawsze opcją.

## <a name="com-component-is-not-installed-on-computer"></a>Składnik COM nie jest zainstalowany na komputerze

Jeśli użytkownik dodał odwołanie do składnika COM, a drugi użytkownik próbuje uruchomić kod na komputerze, na którym nie jest zainstalowany ten składnik, drugi użytkownik otrzyma komunikat o błędzie, że odwołanie zostało przerwane. Zainstalowanie składnika na drugim komputerze spowoduje poprawienie błędu. Aby uzyskać więcej informacji o sposobach używania odwołań do składników COM w projektach, zobacz [współdziałanie com w aplikacjach .NET Framework](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).

## <a name="see-also"></a>Zobacz także

- [Strona odwołań, Projektant projektu (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)