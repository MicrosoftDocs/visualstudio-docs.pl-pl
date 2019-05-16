---
title: Rozwiązywanie problemów z przerwanymi odwołaniami | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- Visual C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
ms.assetid: 00a9ade9-652e-40de-8ada-85f63cd183ee
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a436ffa96e6ca86479bdb5b4f91e30c386acc1a6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689304"
---
# <a name="troubleshooting-broken-references"></a>Rozwiązywanie problemów z przerwanymi odwołaniami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli aplikacja próbuje użyć uszkodzone odwołanie, generowany jest błąd wyjątku. Z brakiem, aby odnaleźć składnika, do którego istnieje odwołanie jest podstawowym wyzwalacza dla błędu, ale istnieje kilka sytuacji, w których odwołanie jest uznawana za uszkodzone. Te wystąpienia są wyświetlane na poniższej liście:  
  
- Ścieżka odwołania projektu jest niepoprawne lub niepełne.  
  
- Usunięto plik, do którego nastąpiło odwołanie.  
  
- Zmieniono nazwę pliku, którego dotyczy odwołanie.  
  
- Połączenie sieciowe lub uwierzytelnianie nie powiodło się.  
  
- Odwołanie jest składnika modelu COM, który nie jest zainstalowany na komputerze.  
  
  Dostępne są następujące środki zaradcze tych problemów.  
  
> [!NOTE]
> Pliki w zestawach są przywoływane przy użyciu ścieżek bezwzględnych w pliku projektu. Dlatego jest możliwe dla użytkowników, którzy pracują w środowisku projektowanie brakuje przywoływanego zestawu w środowisku lokalnym. Aby uniknąć tych błędów, lepiej jest w takich przypadkach można dodać odwołania projektu do projektu. Aby uzyskać więcej informacji, zobacz [NIB jak: Dodawanie lub usuwanie odwołań za pomocą okno dialogowe Dodaj odwołanie](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) i [programowanie za pomocą zestawów](https://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6).  
  
## <a name="reference-path-is-incorrect"></a>Ścieżka odwołania jest nieprawidłowy  
 Jeśli projekty są współdzielone na różnych komputerach, niektóre odwołania nie będzie można znaleźć gdy składnik znajduje się w innym katalogu na każdym komputerze. Odwołania są przechowywane w nazwie pliku składnika (na przykład MyComponent). Po dodaniu odwołania do projektu, lokalizacja folderu pliku składnika (na przykład C:\MyComponents\\) jest dołączany do **ReferencePath** właściwość projektu.  
  
 Po otwarciu projektu próbuje zlokalizować te pliki składnika przez wyszukiwanie w katalogach w ścieżce odwołania. Jeśli projekt jest otwierany na komputerze, na którym są przechowywane w innym katalogu, takie jak D:\MyComponents składnika\\, nie można odnaleźć odwołania i pojawia się błąd, na liście zadań.  
  
 Aby rozwiązać ten problem, możesz usunąć uszkodzone odwołanie i zastąp go za pomocą okna dialogowego Dodaj odwołanie. Innym rozwiązaniem jest użycie **ścieżkę odwołania** elementów na stronach właściwości projektu i zmodyfikować foldery na liście, aby wskazywał poprawne lokalizacje. **Ścieżkę odwołania** właściwość jest trwały dla każdego użytkownika na każdym komputerze. W związku z tym modyfikując ścieżki odniesienia nie ma wpływu na innych użytkowników projektu.  
  
> [!TIP]
> Odwołania projekt projekt nie ma tych problemów. Z tego powodu ich używać zamiast odwołania do pliku, jeśli to możliwe.  
  
#### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Aby naprawić uszkodzone odwołanie, poprawiając ścieżkę odwołania  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i kliknij przycisk **właściwości**.  
  
2. **Projektanta projektu** pojawia się.  
  
3. Jeśli używasz języka Visual Basic, wybierz opcję **odwołania** strony, a następnie kliknij przycisk **ścieżki odwołania** przycisku. W **ścieżki odwołania** okna dialogowego wpisz ścieżkę do folderu, który zawiera element, którego chcesz się odwołać w **folderu** pola, a następnie kliknij przycisk **Dodaj Folder** przycisku.  
  
     —lub—  
  
     Jeśli używasz Visual C#, wybierz opcję **ścieżki odwołania** strony. W **folderu** wpisz ścieżkę do folderu, który zawiera element, który chcesz odwołać, a następnie kliknij przycisk **Dodaj Folder** przycisku.  
  
## <a name="referenced-file-has-been-deleted"></a>Przywoływany plik został usunięty.  
 Jest to możliwe, że plik, do którego nastąpiło odwołanie, został usunięty i już nie istnieje na dysku.  
  
#### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Aby naprawić przerwane odwołanie do pliku, który już nie istnieje na dysku  
  
- Usuń odwołanie.  
  
- Jeśli istnieje odwołanie w innej lokalizacji na komputerze, należy go odczytywać z tej lokalizacji.  
  
- Aby uzyskać więcej informacji, zobacz [NIB jak: Dodawanie lub usuwanie odwołań za pomocą okno dialogowe Dodaj odwołanie](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="referenced-file-has-been-renamed"></a>Nazwa pliku została zmieniona  
 Istnieje możliwość, że zmieniono nazwę pliku, którego dotyczy odwołanie.  
  
#### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Aby naprawić uszkodzone odwołanie do pliku, którego nazwa została zmieniona  
  
- Usuń odwołanie, a następnie dodaj odwołanie do pliku o zmienionej nazwie.  
  
- Odwołanie istnieje w innej lokalizacji na komputerze, należy go odczytywać z tej lokalizacji. Aby uzyskać więcej informacji, zobacz [NIB jak: Dodawanie lub usuwanie odwołań za pomocą okno dialogowe Dodaj odwołanie](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="network-connection-or-authentication-has-failed"></a>Połączenie sieciowe lub uwierzytelnianie nie powiodło się  
 Może istnieć wiele możliwe przyczyny niedostępności plików: połączenie sieciowe nie powiodło się lub niepowodzenie uwierzytelniania, na przykład. Przyczyny dotyczyły, może być unikatowy oznacza, że odzyskiwania; na przykład może być konieczne skontaktuj się z administratorem lokalnym w celu dostępu do wymaganych zasobów. Jednak usunięcie odwołania i naprawianie kodu, których jej jest zawsze opcję. Aby uzyskać więcej informacji, zobacz [NIB jak: Dodawanie lub usuwanie odwołań za pomocą okno dialogowe Dodaj odwołanie](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="com-component-is-not-installed-on-computer"></a>Składnik COM nie jest zainstalowany na komputerze  
 Jeśli użytkownik doda odwołanie do składnika modelu COM, a drugi użytkownik próbuje uruchomić kod na komputerze, na którym nie zainstalowano tego składnika, drugi użytkownik zostanie wyświetlony błąd, czy odwołanie jest uszkodzony. Instalowanie składnika na drugim komputerze spowoduje Popraw błąd. Aby uzyskać więcej informacji o sposobie używania odwołania do składników modelu COM w projektach, zobacz [współdziałanie COM w aplikacjach .NET Framework](https://msdn.microsoft.com/library/f5a72143-c268-4dff-a019-974ad940e17d).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do projektanta projektu](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7)   
 [Strona odwołań, Projektant projektu (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)   
 [NIB jak: Dodawanie lub usuwanie odwołań za pomocą okno dialogowe Dodawanie odwołania](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
