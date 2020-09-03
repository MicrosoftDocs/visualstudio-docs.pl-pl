---
title: Utwórz test usługi sieci Web
ms.date: 06/30/2020
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9934f48e6d5900a418995eb96d357b4ea1ea532f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814762"
---
# <a name="how-to-create-a-web-service-test"></a>Instrukcje: Tworzenie nowego testu usługi internetowej

Aby przetestować usługi sieci Web, można użyć testu wydajności sieci Web. Za pomocą opcji **Wstaw żądanie** i **Wstaw żądanie usługi sieci Web** można dostosować poszczególne żądania w **Edytor internetowego testu wydajnościowego** , aby zlokalizować strony usługi sieci Web. Zwykle te strony nie są wyświetlane w aplikacji sieci Web. W związku z tym należy dostosować żądanie, aby uzyskać do nich dostęp.

>[!NOTE]
> Funkcje testu wydajności i obciążenia sieci Web są przestarzałe w programie Visual Studio 2019. W przypadku Application Insights wieloetapowe testy sieci Web zależą od plików WebTest programu Visual Studio. Zostało [ogłoszone](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/) , że program Visual Studio 2019 będzie ostatnią wersją z funkcjonalnością WebTest. Ważne jest, aby zrozumieć, że podczas gdy nie zostaną dodane żadne nowe funkcje, funkcja WebTest w programie Visual Studio 2019 nadal jest obsługiwana i będzie nadal obsługiwana w ramach cyklu życia produktu. Azure Monitor zespół produkcyjny zakwestionuje pytania dotyczące przyszłościowych [testów dostępności](https://github.com/MicrosoftDocs/azure-docs/issues/26050#issuecomment-468814101)wieloetapowej.

**Wymagania**

Visual Studio Enterprise

## <a name="to-create-a-simple-web-service"></a>Aby utworzyć prostą usługę sieci Web

Aby przetestować, możesz użyć własnej usługi sieci Web lub użyć szablonu usługi Web Basic (ASMX) zawartego w programie Visual Studio. Aby utworzyć prostą usługę sieci Web przy użyciu tego szablonu:

1. W programie Visual Studio Utwórz nowy projekt przy użyciu szablonu aplikacja sieci Web ASP.NET (.NET Framework) i wybierz **pusty** szablon po wyświetleniu monitu. Wpisz nazwę i Utwórz projekt.

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł projektu, wybierz polecenie **Dodaj**  >  **nowy element**, a następnie wybierz pozycję **Usługa sieci Web (ASMX)**. Dodaj usługę sieci Web.

1. Otwórz *WebService1. asmx* i Zastąp domyślną `HelloWorld` metodę sieci Web poniższym kodem.

   ```csharp
   public string HelloWorld(string str)
   {
      return "Hello, " + str;
   }
   ```

## <a name="install-the-load-testing-component"></a>Zainstaluj składnik testowania obciążenia

Jeśli składnik narzędzi testowania wydajności sieci Web i obciążenia nie został jeszcze zainstalowany, należy zainstalować go za pomocą Instalator programu Visual Studio.

1. Otwórz **Instalator programu Visual Studio** z menu **Start** systemu Windows. Możesz również uzyskać do niego dostęp w programie Visual Studio z okna dialogowego Nowy projekt lub wybierając **Narzędzia**  >  **Pobierz narzędzia i funkcje** z paska menu.

1. W **Instalator programu Visual Studio**wybierz kartę **poszczególne składniki** i przewiń w dół do sekcji **debugowanie i testowanie** . Wybierz pozycję **Narzędzia do testowania obciążenia i wydajności sieci Web**.

   ![Składnik narzędzi do testowania wydajności sieci Web i testów obciążenia](media/web-perf-load-testing-tools-component.png)

1. Wybierz przycisk **Modyfikuj** .

   Składnik narzędzi do testowania wydajności sieci Web i testu obciążenia jest zainstalowany.

## <a name="create-a-web-test-project"></a>Utwórz projekt testu sieci Web

Test sieci Web wymaga szablonu projektu test wydajności i obciążenia sieci Web. W tej sekcji utworzymy projekt testu obciążenia języka C#. Możesz również utworzyć projekt testu obciążenia Visual Basic, jeśli wolisz.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

   Jeśli używasz szablonu przykładowej usługi sieci Web (ASMX), możesz dodać projekt testu sieci Web do tego samego rozwiązania.

2. Wybierz pozycję **plik** > **Nowy** > **projekt** z paska menu.

   Zostanie otwarte okno dialogowe **Nowy projekt** .

3. W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowane** i **Visual C#**, a następnie wybierz kategorię **test** . Wybierz szablon **projektu test wydajności i obciążenia sieci Web** .

   ![Szablon projektu testu wydajności i obciążenia sieci Web](media/web-perf-load-test-project-template.png)

4. Wprowadź nazwę projektu, jeśli nie chcesz używać nazwy domyślnej, a następnie wybierz **przycisk OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

   Jeśli używasz szablonu przykładowej usługi sieci Web (ASMX), możesz dodać projekt testu sieci Web do tego samego rozwiązania.

2. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

3. Na stronie **Tworzenie nowego projektu** wpisz **test sieci Web** w polu wyszukiwania, a następnie wybierz szablon **projekt testu wydajności i obciążenia sieci Web jako \[ przestarzały]** dla języka C#. Wybierz pozycję **Next** (Dalej).

4. Wprowadź nazwę projektu, jeśli nie chcesz używać nazwy domyślnej, a następnie wybierz pozycję **Utwórz**.

::: moniker-end

   Program Visual Studio tworzy projekt i wyświetla pliki w **Eksplorator rozwiązań**. Projekt początkowo zawiera jeden plik testu sieci Web o nazwie *WebTest1. webtest*.

## <a name="to-test-a-web-service"></a>Aby przetestować usługę sieci Web

1. Uruchom usługę sieci Web i w razie potrzeby wybierz pozycję **Zatrzymaj** , aby wstrzymać usługę.

1. W projekcie testu sieci Web Otwórz *WebTest1. webtest*, który otwiera Edytor internetowego testu wydajnościowego. W edytorze testów kliknij prawym przyciskiem myszy Test wydajności sieci Web i wybierz polecenie **Dodaj żądanie usługi sieci Web**.

1. W polu właściwości **adres URL** nowego żądania wpisz nazwę usługi sieci Web, na przykład **https://localhost:44318/WebService1.asmx** .

1. W przypadku usługi sieci Web Otwórz oddzielną sesję przeglądarki i wpisz adres URL strony *. asmx* na pasku narzędzi **adres** . W górnej części strony sieci Web Wybierz metodę, którą chcesz przetestować, i Sprawdź komunikat protokołu SOAP. (W przykładowej usłudze sieci Web Metoda to HelloWorld). Po otwarciu metody zobaczysz, że zawiera ona `SOAPAction` .

1. W **Edytor internetowego testu wydajnościowego**kliknij prawym przyciskiem myszy żądanie i wybierz pozycję **Dodaj nagłówek** , aby dodać nowy nagłówek. W właściwości **name** wpisz `SOAPAction` . We właściwości **Value** wpisz wartość, która jest wyświetlana w, na przykład `SOAPAction` *http://tempuri.org/HelloWorld* .

1. Rozwiń węzeł adresu URL w edytorze testów, wybierz węzeł **treść ciąg** i we właściwości **Typ zawartości** wprowadź wartość `text/xml` .

1. Wróć do przeglądarki w kroku 4, wybierz część XML żądania SOAP ze strony Opis usługi sieci Web i skopiuj ją do Schowka.

   Zawartość XML przypomina poniższy przykład:

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
       <soap:Body>
         <HelloWorld xmlns="http://tempuri.org/">
           <str>string</str>
         </HelloWorld>
       </soap:Body>
     </soap:Envelope>
     ```

1. Wróć do Edytor internetowego testu wydajnościowego, a następnie wybierz wielokropek **(...)** we właściwości **treść ciągu** . Wklej zawartość schowka do właściwości.

1. Zastąp wszystkie wartości symboli zastępczych w kodzie XML prawidłowymi wartościami, aby test mógł zostać przekazany. W poprzednim przykładzie zastąpisz wystąpienie o `string` nazwie.

1. Kliknij prawym przyciskiem myszy żądanie usługi sieci Web i wybierz polecenie **Dodaj parametr QueryString adresu URL**.

1. Przypisz parametrowi ciągu zapytania nazwę i wartość. W poprzednim przykładzie nazwa jest `op` i ma wartość `HelloWorld` . Identyfikuje to operację usługi sieci Web, która ma zostać wykonana.

    > [!NOTE]
    > Możesz użyć powiązania danych w treści protokołu SOAP, aby zastąpić dowolną wartość symbolu zastępczego wartościami związanymi z danymi przy użyciu `{{DataSourceName.TableName.ColumnName}}` składni.

1. Uruchom test. W górnym okienku **podglądu wyniki testów wydajności sieci Web**wybierz żądanie usługi sieci Web. W dolnym okienku wybierz kartę **przeglądarka sieci Web** . Zostanie wyświetlony kod XML, który jest zwracany przez usługę sieci Web i wyniki operacji.

   Wyszukaj wyniki żądania usługi sieci Web.

## <a name="see-also"></a>Zobacz też

- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych](../test/create-custom-code-and-plug-ins-for-load-tests.md)
