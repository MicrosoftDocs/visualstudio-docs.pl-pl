---
title: Windows Communication Foundation i usługi danych WCF
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 57b66473333bfe5e22c3f5aca47764bb789a33cd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045191"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio

Visual Studio zapewnia narzędzia do pracy z Windows Communication Foundation (WCF) i usługi danych WCF, technologii firmy Microsoft do tworzenia aplikacji rozproszonej. Ten temat zawiera wprowadzenie do usługi z punktu widzenia programu Visual Studio. Aby uzyskać pełną dokumentację, zobacz [4.5 usług danych WCF](/dotnet/framework/data/wcf/index).

## <a name="what-is-wcf"></a>Co to jest WCF?

Windows Communication Foundation (WCF) to ujednolicone umożliwiająca tworzenie bezpieczne, niezawodne, transakcyjne i interoperacyjne rozproszonych aplikacji. Zastępuje starsze technologie komunikacji międzyprocesowej, takich jak usługi sieci web ASMX wywołaniem funkcji zdalnych .NET, usługi Enterprise (DCOM) i usługi MSMQ. Usługi WCF łączy funkcje tych technologii pod ujednolicony model programowania. Upraszcza to środowisko tworzenia aplikacji rozproszonej.

### <a name="what-are-wcf-data-services"></a>Co to są usługi danych WCF

Usługi danych WCF jest implementacją standardowego protokołu Open Data (OData).  Usługi danych WCF umożliwia udostępnianie danych tabelarycznych jako zestaw interfejsów API REST, co pozwala zwracanych danych przy użyciu standardowych poleceń HTTP, takich jak pobieranie, POST, PUT lub usunąć. Po stronie serwera, usługi danych WCF są zastępowane przez [ASP.NET Web API](http://www.asp.net/web-api) do tworzenia nowych usług OData. Biblioteka klienta usługi danych WCF w dalszym ciągu jest dobrym wyborem, co umożliwia korzystanie z usługi OData w aplikacji .NET w programie Visual Studio (**projektu** > **Dodaj odwołanie do usługi**). Aby uzyskać więcej informacji, zobacz [4.5 usług danych WCF](http://go.microsoft.com/fwlink/?LinkID=119952).

### <a name="wcf-programming-model"></a>Model programowania programu WCF

Model programowania WCF opiera się na komunikację między dwiema jednostkami: usługi WCF i klienta WCF. Model programowania jest hermetyzowany w <xref:System.ServiceModel> przestrzeni nazw w programie .NET Framework.

### <a name="wcf-service"></a>Usługa WCF

Usługa WCF opiera się na interfejs, który definiuje kontrakt między usługą i klienta. Jest on oznaczony wartością <xref:System.ServiceModel.ServiceContractAttribute> atrybutu, jak pokazano w poniższym kodzie:

[!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
[!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]

Definiowanie funkcji lub metody, które są udostępniane przez usługę WCF, oznaczając je <xref:System.ServiceModel.OperationContractAttribute> atrybutu.

[!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
[!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]

Ponadto należy udostępnić dane serializowane, oznaczając typu złożonego z <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu. Umożliwia to powiązanie danych w kliencie.

Po zdefiniowaniu interfejs i jego metod one są hermetyzowane w klasie, która implementuje interfejs. Jednej klasy usługi WCF można zaimplementować wiele kontraktów usług.

Usługa WCF jest uwidaczniany dla zużycia, przez co jest nazywane *punktu końcowego*. Punkt końcowy zapewnia jedynym sposobem, aby komunikować się z usługą; nie możesz uzyskać dostępu usługi za pośrednictwem odwołanie bezpośrednie tak jak w przypadku innych klas.

Punkt końcowy składa się z adresu, powiązanie i kontrakt. Określa adres, gdzie znajduje się usługa; może to być adres URL, adresu FTP lub sieci lub ścieżkę lokalną. Powiązanie definiuje sposób komunikacji z usługą. Powiązania WCF zapewniają wszechstronny modelu do określania protokołów, takich jak HTTP lub FTP mechanizmu zabezpieczeń, takie jak uwierzytelnianie Windows lub nazwy użytkownika i hasła i wiele więcej. Kontrakt obejmuje operacje, które są udostępniane przez klasy usługi WCF.

Wiele punktów końcowych mogą być udostępniane dla jednej usługi WCF. Dzięki temu różnych klientów do komunikowania się z tą samą usługą na różne sposoby. Na przykład usługi bankowe może zapewnia jeden punkt końcowy dla pracowników i inny dla klientów zewnętrznych przy użyciu innego adresu, powiązania i/lub kontraktu.

### <a name="wcf-client"></a>Klienta programu WCF

Klienta programu WCF składa się z *proxy* , który umożliwia aplikacji do komunikowania się z usługą WCF, a punkt końcowy, który odpowiada punkt końcowy zdefiniowany dla usługi. Serwer proxy jest generowany po stronie klienta w *app.config* plik i zawiera informacje na temat typów i metod, które są udostępniane przez usługę. W przypadku usług, które udostępniają wiele punktów końcowych klienta można wybrać jedną, która najlepiej pasuje do swoich potrzeb, na przykład do komunikowania się za pośrednictwem protokołu HTTP i korzystać z uwierzytelniania Windows.

Po utworzeniu klienta programu WCF możesz odwoływać się usługi w kodzie tak samo jak każdy inny obiekt. Na przykład, aby wywołać `GetData` metoda przedstawionej wcześniej, należy napisać kod, który jest podobny do następującego:

[!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
[!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]

## <a name="wcf-tools-in-visual-studio"></a>Narzędzia WCF w programie Visual Studio

Visual Studio zapewnia narzędzia ułatwiające tworzenie usług WCF i klienci WCF. Aby uzyskać wskazówki, który demonstruje narzędzia, zobacz [instruktażu: Tworzenie prostą usługę WCF w formularzach Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="create-and-test-wcf-services"></a>Tworzenie i testowanie usług WCF

Szablony programu Visual Studio WCF jako podstawa umożliwia szybkie tworzenie własnej usługi. Następnie służy hostów Auto usługi WCF i WCF przetestować klienta do debugowania i testowania tej usługi. Razem te narzędzia zapewniają szybki i wygodny debugowania i cyklu testowania i wyeliminować konieczność zaangażowani w zapewnienie modelu hostingu na wczesnym etapie.

#### <a name="wcf-templates"></a>Szablony programu WCF

Szablony programu Visual Studio WCF stanowią strukturę podstawowe klasy do tworzenia aplikacji usługi. Kilka szablonów WCF jest dostępna w **Dodaj nowy projekt** okno dialogowe. Obejmują one projekty lLibrary usługi WCF, witryn sieci Web WCF usługi i szablony elementów usług WCF.

Po wybraniu szablonu, pliki zostaną dodane dla kontraktu usługi, implementacji usługi i konfigurację usługi. Wszystkie niezbędne atrybuty zostały już dodane, tworzenie prostego typu "Hello World", usługi i nie miał pisania kodu. Będzie oczywiście, chcesz dodać kod, aby zapewnić funkcji i metod usługi rzeczywistych, ale Szablony stanowią podstawę podstawowe.

Aby dowiedzieć się więcej na temat szablonów usługi WCF, zobacz [szablony programu Visual Studio WCF](/dotnet/framework/wcf/wcf-vs-templates).

#### <a name="wcf-service-host"></a>Host usługi WCF

Po uruchomieniu debugera programu Visual Studio (naciskając **F5**) dla projektu usługi WCF, narzędzie Host usługi WCF zostanie automatycznie uruchomiony do hostowania usługi lokalnie. Host usługi WCF wylicza usługi w projekcie usługi WCF, ładuje tej konfiguracji projektu, a następnie tworzy wystąpienie hosta dla każdej usługi, które znajdzie.

Za pomocą Host usługi WCF, możesz przetestować bez pisania dodatkowego kodu lub zatwierdzania do określonego hosta podczas tworzenia usługi WCF.

Aby dowiedzieć się więcej na temat Host usługi WCF, zobacz [host usługi WCF (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).

#### <a name="wcf-test-client"></a>Klient testowy WCF

Narzędzia WCF przetestować klienta umożliwia badanie parametrów wejściowych, przesyłanie, że dane wejściowe do usługi WCF i wyświetlić odpowiedź, którą usługa wysyła z powrotem. Zapewnia wygodne usługi testowania środowisko podczas łączenia z hostem usługi WCF. Znajdź narzędzia w *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE* folderu.

Po naciśnięciu klawisza **F5** Aby debugować projekt usługi WCF, klient testowy WCF otwiera i wyświetla listę punktów końcowych usługi, które są zdefiniowane w pliku konfiguracji. Można przetestować parametrów i uruchom usługę i powtórz ten proces nieprzerwanie testować i weryfikować usługi.

Aby dowiedzieć się więcej na temat klienta programu WCF testu, zobacz [WCF przetestować klienta (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).

### <a name="accessing-wcf-services-in-visual-studio"></a>Dostęp do usług WCF w programie Visual Studio

Program Visual Studio upraszcza proces tworzenia klienci WCF, automatycznego generowania serwera proxy i punkt końcowy dla usług, które możesz dodać za pomocą **Dodaj odwołanie do usługi** okno dialogowe. Wszystkich niezbędnych informacji konfiguracyjnych zostanie dodany do *app.config* pliku. Większość przypadków wszystko, co należy zrobić to utworzenia wystąpienia usługi do jej używania.

**Dodaj odwołanie do usługi** okno dialogowe umożliwia wprowadź adres dla usługi lub Wyszukaj to usługa, która jest zdefiniowana w rozwiązaniu. Okno dialogowe zwraca listę usług i operacje udostępniane przez te usługi. Umożliwia on również definiowanie przestrzeni nazw za pomocą którego można będzie odwoływać się do usługi w kodzie.

**Konfigurowanie odwołania do usług** okno dialogowe umożliwia dostosowanie konfigurację dla usługi. Można zmienić adres usługi, określ poziom dostępu, zachowanie asynchroniczne i typy kontraktu komunikatu i konfigurować ponowne użycie typu.

## <a name="how-to-select-a-service-endpoint"></a>Instrukcje: Wybierz punkt końcowy usługi

Niektóre usługi Windows Communication Foundation (WCF) ujawniają wiele punktów końcowych, za pomocą których klient może komunikować się z usługą. Na przykład usługa może narazić jeden punkt końcowy, który używa powiązanie HTTP i nazwę użytkownika i hasło zabezpieczeń i drugi punkt końcowy, który korzysta z protokołu FTP i uwierzytelniania Windows. Pierwszy punkt końcowy mogą być używane przez aplikacje uzyskujące dostęp do usługi z poza zaporą, podczas gdy drugi mogą być używane w sieci intranet.

W takim przypadku można określić `endpointConfigurationName` jako parametr do konstruktora dla odwołania do usługi.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>Aby wybrać punkt końcowy usługi

1. Dodaj odwołanie do usługi WCF, klikając prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierając pozycję **Dodaj odwołanie do usługi**.

2. W edytorze kodu Dodaj Konstruktor dla odwołania do usługi:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Zastąp *ServiceReference* z przestrzenią nazw dla odwołania do usługi i Zastąp *Service1Client* przy użyciu nazwy usługi.

3. Lista IntelliSense wyświetla obejmującą przeciążenia dla konstruktora. Wybierz `endpointConfigurationName As String` przeciążenia.

4. Następujące przeciążenia, wpisz `=` *ConfigurationName*, gdzie *ConfigurationName* to nazwa punktu końcowego, który chcesz użyć.

    > [!NOTE]
    > Jeśli nie znasz nazwy dostępnych punktów końcowych, możesz je znaleźć w *app.config* pliku.

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Aby znaleźć dostępne punkty końcowe dla usługi WCF

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **app.config** pliku projektu, który zawiera odwołanie do usługi, a następnie kliknij przycisk **Otwórz**. Plik zostanie wyświetlony w edytorze kodu.

2. Wyszukaj `<Client>` tagu w pliku.

3. Wyszukiwanie poniżej `<Client>` tag w przypadku znaczników, który zaczyna się od `<Endpoint>`.

     Jeśli odwołanie do usługi zawiera wiele punktów końcowych, będzie co najmniej dwóch `<Endpoint` tagów.

4. Wewnątrz `<EndPoint>` tagu, można znaleźć `name="` *SomeService* `"` parametru (gdzie *SomeService* reprezentuje nazwę punktu końcowego). Jest to nazwa punktu końcowego, który może być przekazywany do `endpointConfigurationName As String` przeciążenia konstruktora odwołania do usługi.

## <a name="how-to-call-a-service-method-asynchronously"></a>Instrukcje: Asynchroniczne wywoływanie metody usługi

Większość metod w usług Windows Communication Foundation (WCF) może zostać wywołana synchronicznie lub asynchronicznie. Asynchroniczne wywołanie metody umożliwia aplikacji, aby kontynuować pracę, podczas gdy metoda jest wywoływana, gdy działa przez wolne połączenie.

Domyślnie gdy odwołanie do usługi zostanie dodany do projektu, go jest skonfigurowany do wywołania metod synchronicznie. Można zmienić to zachowanie asynchroniczne wywoływanie metod, zmieniając ustawienia w **Konfiguruj odwołanie do usługi** okno dialogowe.

> [!NOTE]
> Ta opcja jest ustawiona na podstawie za daną usługę. Jeśli jedna metoda usługi nosi nazwę asynchronicznej, wszystkie metody musi zostać wywołana asynchronicznie.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>Do wywołania metody usługi asynchronicznie

1. W **Eksploratora rozwiązań**, wybierz odwołanie do usługi.

2. Na **projektu** menu, kliknij przycisk **Konfiguruj odwołanie do usługi**.

3. W **Konfiguruj odwołanie do usługi** okno dialogowe, wybierz opcję **Eneruj operacje asynchroniczne** pole wyboru.

## <a name="how-to-bind-data-returned-by-a-service"></a>Instrukcje: Powiązanie danych zwracanych przez usługę

Można powiązać danych zwracanych przez usługę Windows Communication Foundation (WCF) do formantu, tak samo, jak dowolnego innego źródła danych można powiązać formant. Po dodaniu odwołania do usługi WCF, jeśli usługa zawiera złożone typy, które zwracają dane, są automatycznie dodawane do **źródeł danych** okna.

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Aby powiązać formant jedno pole danych zwracane przez usługę WCF

1. Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.

   **Źródeł danych** zostanie wyświetlone okno.

2. W **źródeł danych** okna, rozwiń węzeł odwołania do usługi. Złożone typy zwracane przez wyświetlanie usługi.

3. Rozwiń węzeł dla typu. Pola danych dla tego typu są wyświetlane.

4. Wybierz pole i kliknij strzałkę listy rozwijanej, aby wyświetlić listę elementów sterujących, które są dostępne dla typu danych.

5. Kliknij formant, z którą chcesz powiązać.

6. Przeciągnij pole do formularza. Formant został dodany do formularza, wraz z <xref:System.Windows.Forms.BindingSource> składnika i <xref:System.Windows.Forms.BindingNavigator> składnika.

7. Powtórz kroki od 4, chociaż 6 dla innych pól, które chcesz powiązać.

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Aby powiązać formant typu złożonego, zwracane przez usługę WCF

1. Na **danych** menu, wybierz opcję **Pokaż źródła danych**. **Źródeł danych** zostanie wyświetlone okno.

2. W **źródeł danych** okna, rozwiń węzeł odwołania do usługi. Złożone typy zwracane przez wyświetlanie usługi.

3. Wybierz węzeł dla typu, a następnie kliknij strzałkę listy rozwijanej, aby wyświetlić listę dostępnych opcji.

4. Kliknij opcję **DataGridView** do wyświetlania danych w siatce lub **szczegóły** do wyświetlania danych w poszczególnych formantów.

5. Przeciągnij węzeł na formularzu. Formanty są dodawane do formularza, wraz z <xref:System.Windows.Forms.BindingSource> składnika i <xref:System.Windows.Forms.BindingNavigator> składnika.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Instrukcje: Konfigurowanie usługi do ponownego użycia istniejących typów

Po dodaniu do projektu odwołanie do usługi żadnych typów zdefiniowanych w usłudze są generowane w projekcie lokalnym. W wielu przypadkach tworzy to typy zduplikowanych, gdy usługa korzysta z wspólnego typów programu .NET Framework lub gdy typy są definiowane w bibliotece udostępnionej.

Aby uniknąć tego problemu, typów w przywoływanych zestawach są udostępnione domyślnie. Jeśli chcesz wyłączyć udostępnianie dla jednego lub więcej zestawów typu, możesz zrobić to w **Konfigurowanie odwołania do usług** okno dialogowe.

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Aby wyłączyć udostępnianie typu w jednym zestawie

1. W **Eksploratora rozwiązań**, wybierz odwołanie do usługi.

2. Na **projektu** menu, kliknij przycisk **Konfiguruj odwołanie do usługi**.

3. W **Konfigurowanie odwołania do usług** okno dialogowe, wybierz opcję **ponownie użyj typów w określonych przywoływanych zestawach**.

4. Zaznacz pole wyboru dla każdego zestawu, w której chcesz włączyć udostępnianie typu. Aby wyłączyć udostępnianie dla zestawu typu, to pole wyboru zostanie wyczyszczone.

### <a name="to-disable-type-sharing-in-all-assemblies"></a>Aby wyłączyć udostępnianie typu w wszystkie zestawy

1. W **Eksploratora rozwiązań**, wybierz odwołanie do usługi.

2. Na **projektu** menu, kliknij przycisk **Konfiguruj odwołanie do usługi**.

3. W **Konfigurowanie odwołania do usług** okno dialogowe wyczyść **ponownie użyj typów w przywoływanych zestawach** pole wyboru.

## <a name="related-topics"></a>Tematy pokrewne

| Tytuł | Opis |
| - | - |
| [Przewodnik: Tworzenie prostej usługi WCF w modelu Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | Zawiera instrukcje krok po kroku Pokaz tworzenia i używania usług WCF w programie Visual Studio. |
| [Przewodnik: Tworzenie usługi danych programu WCF za pomocą struktur WPF i Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | Zawiera pokaz krok po kroku dotyczące tworzenia i używania usług danych WCF w programie Visual Studio. |
| [Używanie narzędzi deweloperskich programu WCF](/dotnet/framework/wcf/using-the-wcf-development-tools) | W tym artykule omówiono sposób tworzenia i testowania usługi WCF w programie Visual Studio. |
| | [Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołań usługi danych WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [Rozwiązywanie problemów z odwołaniami usługi](../data-tools/troubleshooting-service-references.md) | Przedstawia informacje o typowych błędów, które mogą wystąpić, za pomocą odwołań do usług i sposobu zapobiegania im. |
| [Debugowanie usług WCF](../debugger/debugging-wcf-services.md) | Zawiera opis typowych problemów debugowania i technik, które mogą wystąpić podczas debugowania usług WCF. |
| [Przewodnik: Tworzenie aplikacji warstwowych](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | Instrukcje krok po kroku dotyczące tworzenia typizowany zestaw danych i oddzielenie kodu TableAdapter i zestaw danych do wielu projektów. |
| [Konfigurowanie odwołania do usługi, okno dialogowe](../data-tools/configure-service-reference-dialog-box.md) | W tym artykule opisano elementy interfejsu użytkownika z **Konfiguruj odwołanie do usługi** okno dialogowe. |

## <a name="reference"></a>Tematy pomocy

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>Zobacz także

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)