---
title: Windows Communication Foundation i WCF Data Services
description: Eksplorowanie usług Windows Communication Foundation (WCF) i WCF Data Services w programie Visual Studio, dzięki czemu można tworzyć aplikacje rozproszone.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 45ff4336859fe0294232e9ca1d99513665d8e975
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216478"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio

Program Visual Studio udostępnia narzędzia do pracy z usługami Windows Communication Foundation (WCF) i WCF Data Services, technologii firmy Microsoft do tworzenia aplikacji rozproszonych. Ten temat zawiera wprowadzenie do usług z perspektywy programu Visual Studio. Aby uzyskać pełną dokumentację, zobacz [WCF Data Services 4,5](/dotnet/framework/data/wcf/index).

## <a name="what-is-wcf"></a>Co to jest WCF?

Windows Communication Foundation (WCF) to ujednolicona platforma służąca do tworzenia bezpiecznych, niezawodnych, transakcyjnych i międzyoperacyjnych aplikacji rozproszonych. Zastępuje ona starsze technologie komunikacji międzyprocesowej, takie jak usługi sieci Web ASMX, komunikacja zdalna platformy .NET, usługi dla przedsiębiorstw (DCOM) i MSMQ. Funkcja WCF łączy wszystkie te technologie w ramach ujednoliconego modelu programowania. Upraszcza to środowisko tworzenia aplikacji rozproszonych.

### <a name="what-are-wcf-data-services"></a>Co to są WCF Data Services

WCF Data Services to implementacja standardu protokołu Open Data (OData).  WCF Data Services pozwala uwidocznić dane tabelaryczne jako zestaw interfejsów API REST, co umożliwia Zwracanie danych przy użyciu standardowych czasowników HTTP, takich jak GET, POST, PUT i DELETE. Po stronie serwera WCF Data Services są zastępowane przez [interfejs API sieci Web ASP.NET](https://dotnet.microsoft.com/apps/aspnet/apis) na potrzeby tworzenia nowych usług OData. Biblioteka klienta WCF Data Services nadal jest dobrym rozwiązaniem w przypadku korzystania z usług OData w aplikacji .NET z programu Visual Studio (**Project**  >  **Dodaj odwołanie do usługi**). Aby uzyskać więcej informacji, zobacz [WCF Data Services 4,5](/dotnet/framework/data/wcf).

### <a name="wcf-programming-model"></a>Model programowania WCF

Model programowania WCF jest oparty na komunikacji między dwiema jednostkami: usługą WCF i klientem programu WCF. Model programowania jest hermetyzowany w <xref:System.ServiceModel> przestrzeni nazw programu .NET.

### <a name="wcf-service"></a>Usługa WCF

Usługa WCF jest oparta na interfejsie, który definiuje kontrakt między usługą a klientem. Jest oznaczona <xref:System.ServiceModel.ServiceContractAttribute> atrybutem, jak pokazano w poniższym kodzie:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs" id="Snippet6":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb" id="Snippet6":::

Definiujesz funkcje lub metody, które są uwidaczniane przez usługę WCF, oznaczając je <xref:System.ServiceModel.OperationContractAttribute> atrybutem.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs" id="Snippet1":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb" id="Snippet1":::

Ponadto można uwidocznić dane serializowane, zaznaczając typ złożony z <xref:System.Runtime.Serialization.DataContractAttribute> atrybutem. Pozwala to na powiązanie danych w kliencie.

Po zdefiniowaniu interfejsu i jego metod są one hermetyzowane w klasie, która implementuje interfejs. Pojedyncza Klasa usługi WCF może zaimplementować wiele kontraktów usługi.

Usługa WCF jest udostępniona do użycia na podstawie tego, co jest znane jako *punkt końcowy*. Punkt końcowy zapewnia jedyny sposób komunikowania się z usługą; nie można uzyskać dostępu do usługi za pośrednictwem bezpośredniego odwołania, tak jak w przypadku innych klas.

Punkt końcowy składa się z adresu, powiązania i kontraktu. Adres określa miejsce, w którym znajduje się usługa; może to być adres URL, adres FTP lub sieć lub ścieżka lokalna. Powiązanie definiuje sposób komunikacji z usługą. Powiązania WCF zapewniają wszechstronny model służący do określania protokołu, takiego jak HTTP lub FTP, mechanizm zabezpieczeń, taki jak uwierzytelnianie systemu Windows lub nazwy użytkowników i hasła, a także wiele innych. Kontrakt obejmuje operacje, które są udostępniane przez klasę usługi WCF.

Dla pojedynczej usługi WCF można uwidocznić wiele punktów końcowych. Umożliwia to różnym klientom komunikowanie się z tą samą usługą na różne sposoby. Na przykład usługa bankowości może udostępnić jeden punkt końcowy dla pracowników i drugi dla klientów zewnętrznych, z których każdy korzysta z innego adresu, powiązania i/lub kontraktu.

### <a name="wcf-client"></a>Klient WCF

Klient WCF składa się z *serwera proxy* , który umożliwia aplikacji komunikację z usługą WCF oraz punkt końcowy, który jest zgodny z punktem końcowym zdefiniowanym dla usługi. Serwer proxy jest generowany po stronie klienta w pliku *app.config* i zawiera informacje o typach i metodach, które są udostępniane przez usługę. W przypadku usług, które uwidaczniają wiele punktów końcowych, klient może wybrać ten, który najlepiej odpowiada potrzebom, na przykład w celu komunikowania się za pośrednictwem protokołu HTTP i używania uwierzytelniania systemu Windows.

Po utworzeniu klienta WCF należy odwołać się do usługi w kodzie tak samo jak każdy inny obiekt. Na przykład, aby wywołać `GetData` metodę przedstawioną wcześniej, należy napisać kod, który będzie wyglądać następująco:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs" id="Snippet3":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb" id="Snippet3":::

## <a name="wcf-tools-in-visual-studio"></a>Narzędzia WCF w programie Visual Studio

Program Visual Studio zawiera narzędzia, które ułatwiają tworzenie zarówno usług WCF, jak i klientów programu WCF. Aby zapoznać się z przewodnikiem, który demonstruje narzędzia, zobacz [Przewodnik: tworzenie prostej usługi WCF w Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="create-and-test-wcf-services"></a>Tworzenie i testowanie usług WCF

Możesz użyć szablonów programu WCF Visual Studio jako podstawy, aby szybko utworzyć własną usługę. Do debugowania i testowania usługi można użyć usługi WCF i klienta testowego WCF. Narzędzia te wspólnie zapewniają szybkie i wygodne cykle debugowania i testowania oraz eliminują wymóg zatwierdzania modelu hostingu na wczesnym etapie.

#### <a name="wcf-templates"></a>Szablony WCF

Szablony Visual Studio programu WCF zapewniają podstawową strukturę klasy do tworzenia usług. Kilka szablonów WCF jest dostępnych w oknie dialogowym **Dodaj nowy projekt** . Obejmują one projekty usługi WCF lLibrary, witryny usługi WCF i szablony elementów usługi WCF.

Po wybraniu szablonu dodawane są pliki dla kontraktu usługi, implementacji usługi i konfiguracji usługi. Wszystkie niezbędne atrybuty zostały już dodane, Tworzenie prostego typu "Hello world" usługi i nie trzeba pisać żadnego kodu. Oczywiście warto dodać kod, aby zapewnić funkcje i metody dla rzeczywistej usługi światowej, ale szablony stanowią podstawową podstawę.

Aby dowiedzieć się więcej na temat szablonów usługi WCF, zobacz [szablony Visual Studio programu WCF](/dotnet/framework/wcf/wcf-vs-templates).

#### <a name="wcf-service-host"></a>Host usługi WCF

Po uruchomieniu debugera programu Visual Studio (przez naciśnięcie klawisza **F5**) dla projektu usługi WCF narzędzie hosta usługi WCF zostanie automatycznie uruchomione, aby hostować usługę lokalnie. Host usługi WCF wylicza usługi w projekcie usługi WCF, ładuje konfigurację projektu i tworzy wystąpienie hosta dla każdej znalezionej usługi.

Korzystając z hosta usługi WCF, można testować usługę WCF bez konieczności pisania dodatkowego kodu lub zatwierdzania do określonego hosta podczas opracowywania.

Aby dowiedzieć się więcej na temat hosta usługi WCF, zobacz [host usługi WCF (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).

#### <a name="wcf-test-client"></a>Klient testowy WCF

Narzędzie klienta testowego WCF umożliwia wprowadzanie parametrów testowych, przesyłanie tych danych wejściowych do usługi WCF oraz wyświetlanie odpowiedzi wysyłanej przez usługę. Zapewnia wygodne środowisko testowania usług, łącząc je z hostem usługi WCF. Znajdź narzędzie w folderze *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE* .

Po naciśnięciu klawisza **F5** w celu debugowania projektu usługi WCF zostanie otwarty klient testowy WCF i zostanie wyświetlona lista punktów końcowych usługi, które są zdefiniowane w pliku konfiguracji. Można przetestować parametry i uruchomić usługę i powtórzyć ten proces w celu ciągłego testowania i weryfikowania usługi.

Aby dowiedzieć się więcej o kliencie testowym WCF, zobacz [klienta testowego WCF (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).

### <a name="accessing-wcf-services-in-visual-studio"></a>Uzyskiwanie dostępu do usług WCF w programie Visual Studio

Program Visual Studio upraszcza zadanie tworzenia klientów WCF, automatycznie generując serwer proxy i punkt końcowy dla usług, które można dodać przy użyciu okna dialogowego **Dodaj odwołanie do usługi** . Wszystkie niezbędne informacje o konfiguracji są dodawane do pliku *app.config* . W większości przypadków wszystkie czynności, które należy wykonać, są wystąpieniem usługi, aby można było z niej korzystać.

Okno dialogowe **Dodaj odwołanie do usługi** umożliwia wprowadzenie adresu usługi lub wyszukanie usługi zdefiniowanej w rozwiązaniu. Okno dialogowe zwraca listę usług i operacje udostępniane przez te usługi. Umożliwia także zdefiniowanie przestrzeni nazw, za pomocą której będziesz odwoływać się do usług w kodzie.

Okno dialogowe **Konfigurowanie odwołań do usług** umożliwia dostosowanie konfiguracji usługi. Można zmienić adres usługi, określić poziom dostępu, zachowanie asynchroniczne i typy kontraktu komunikatów oraz ponownie skonfigurować typ.

## <a name="how-to-select-a-service-endpoint"></a>Instrukcje: Wybieranie punktu końcowego usługi

Niektóre usługi Windows Communication Foundation (WCF) uwidaczniają wiele punktów końcowych, za pomocą których klient może komunikować się z usługą. Na przykład usługa może uwidocznić jeden punkt końcowy, który używa powiązania HTTP i nazwy użytkownika i hasła oraz drugi punkt końcowy, który używa uwierzytelniania za pomocą protokołu FTP i systemu Windows. Pierwszy punkt końcowy może być używany przez aplikacje, które uzyskują dostęp do usługi spoza zapory, podczas gdy druga może być używana w intranecie.

W takim przypadku można określić `endpointConfigurationName` jako parametr do konstruktora dla odwołania do usługi.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>Aby wybrać punkt końcowy usługi

1. Aby dodać odwołanie do usługi WCF, kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj odwołanie do usługi**.

2. W edytorze kodu Dodaj Konstruktor dla odwołania do usługi:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Zastąp wartość *ServiceReference* z przestrzenią nazw dla odwołania do usługi i Zastąp *Service1Client* nazwą usługi.

3. Zostanie wyświetlona lista IntelliSense, która zawiera przeciążenia dla konstruktora. Wybierz `endpointConfigurationName As String` Przeciążenie.

4. Po przeciążeniu wpisz `=` *ConfigurationName*, gdzie *ConfigurationName* jest nazwą punktu końcowego, którego chcesz użyć.

    > [!NOTE]
    > Jeśli nie znasz nazw dostępnych punktów końcowych, możesz je znaleźć w pliku *app.config* .

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Aby znaleźć dostępne punkty końcowe dla usługi WCF

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik **app.config** dla projektu, który zawiera odwołanie do usługi, a następnie kliknij polecenie **Otwórz**. Plik jest wyświetlany w edytorze kodu.

2. Wyszukaj `<Client>` tag w pliku.

3. Wyszukaj pod `<Client>` tagiem tag, który rozpoczyna się od `<Endpoint>` .

     Jeśli odwołanie do usługi zawiera wiele punktów końcowych, będą dostępne co najmniej dwa `<Endpoint` Tagi.

4. Wewnątrz `<EndPoint>` znacznika znajduje się `name="`  `"` parametr SomeService (gdzie *SomeService* reprezentuje nazwę punktu końcowego). Jest to nazwa punktu końcowego, który może zostać przesłany do `endpointConfigurationName As String` przeciążenia konstruktora dla odwołania do usługi.

## <a name="how-to-call-a-service-method-asynchronously"></a>Instrukcje: Asynchroniczne wywoływanie metody usługi

Większość metod w usługach Windows Communication Foundation (WCF) może być wywoływana synchronicznie lub asynchronicznie. Wywołanie metody asynchronicznej pozwala aplikacji na kontynuowanie pracy, gdy metoda jest wywoływana, gdy działa przez wolne połączenie.

Domyślnie, gdy odwołanie do usługi jest dodawane do projektu, jest skonfigurowane do wywołania metod synchronicznie. Można zmienić zachowanie, aby wywołać metody asynchronicznie, zmieniając ustawienie w oknie dialogowym **Konfigurowanie odwołania do usługi** .

> [!NOTE]
> Ta opcja jest ustawiana dla poszczególnych usług. Jeśli jedna metoda dla usługi jest wywoływana asynchronicznie, wszystkie metody muszą być wywoływane asynchronicznie.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>Aby wywołać metodę usługi asynchronicznie

1. W **Eksplorator rozwiązań** wybierz odwołanie do usługi.

2. W menu **projekt** kliknij polecenie **Konfiguruj odwołanie do usługi**.

3. W oknie dialogowym **Konfigurowanie odwołania do usługi** zaznacz pole wyboru **Generuj operacje asynchroniczne** .

## <a name="how-to-bind-data-returned-by-a-service"></a>Instrukcje: wiązanie danych zwróconych przez usługę

Dane zwrócone przez usługę Windows Communication Foundation (WCF) można powiązać z kontrolką tak samo jak powiązanie dowolnego innego źródła danych z kontrolką. Po dodaniu odwołania do usługi WCF, jeśli usługa zawiera złożone typy, które zwracają dane, są one automatycznie dodawane do okna **źródła danych** .

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Aby powiązać formant z polem danych pojedynczym zwracanym przez usługę WCF

1. W menu **dane** kliknij przycisk **Pokaż źródła danych**.

   Zostanie wyświetlone okno **źródła danych** .

2. W oknie **źródła danych** rozwiń węzeł odwołania do usługi. Wszystkie typy złożone zwracane przez wyświetlanie usługi.

3. Rozwiń węzeł typu. Wyświetlane są pola danych dla tego typu.

4. Zaznacz pole i kliknij strzałkę listy rozwijanej, aby wyświetlić listę kontrolek dostępnych dla danego typu danych.

5. Kliknij typ formantu, z którym chcesz utworzyć powiązanie.

6. Przeciągnij pole na formularz. Kontrolka jest dodawana do formularza wraz ze <xref:System.Windows.Forms.BindingSource> składnikiem i <xref:System.Windows.Forms.BindingNavigator> składnikiem.

7. Powtórz kroki od 4 do 6 dla innych pól, które chcesz powiązać.

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Aby powiązać formant z typem złożonym zwracanym przez usługę WCF

1. W menu **dane** wybierz pozycję **Pokaż źródła danych**. Zostanie wyświetlone okno **źródła danych** .

2. W oknie **źródła danych** rozwiń węzeł odwołania do usługi. Wszystkie typy złożone zwracane przez wyświetlanie usługi.

3. Wybierz węzeł dla typu i kliknij strzałkę listy rozwijanej, aby wyświetlić listę dostępnych opcji.

4. Kliknij **formant DataGridView** , aby wyświetlić dane w siatce lub **szczegóły** , aby wyświetlić dane w poszczególnych kontrolkach.

5. Przeciągnij węzeł na formularz. Kontrolki są dodawane do formularza wraz ze <xref:System.Windows.Forms.BindingSource> składnikiem i <xref:System.Windows.Forms.BindingNavigator> składnikiem.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Instrukcje: Konfigurowanie usługi do ponownego użycia istniejących typów

Gdy odwołanie do usługi zostanie dodane do projektu, wszystkie typy zdefiniowane w usłudze są generowane w projekcie lokalnym. W wielu przypadkach tworzy zduplikowane typy, gdy usługa używa popularnych typów .NET lub gdy typy są zdefiniowane w bibliotece udostępnionej.

Aby uniknąć tego problemu, typy w przywoływanych zestawach są domyślnie udostępniane. Jeśli chcesz wyłączyć udostępnianie typu dla jednego lub kilku zestawów, możesz to zrobić w oknie dialogowym **Konfigurowanie odwołań do usługi** .

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Aby wyłączyć udostępnianie typu w pojedynczym zestawie

1. W **Eksplorator rozwiązań** wybierz odwołanie do usługi.

2. W menu **projekt** kliknij polecenie **Konfiguruj odwołanie do usługi**.

3. W oknie dialogowym **Konfigurowanie odwołań do usług** wybierz pozycję **Użyj ponownie typów w określonych przywoływanych zestawach**.

4. Zaznacz pole wyboru dla każdego zestawu, w którym chcesz włączyć udostępnianie typu. Aby wyłączyć udostępnianie typu dla zestawu, pozostaw zaznaczone pole wyboru.

### <a name="to-disable-type-sharing-in-all-assemblies"></a>Aby wyłączyć udostępnianie typu we wszystkich zestawach

1. W **Eksplorator rozwiązań** wybierz odwołanie do usługi.

2. W menu **projekt** kliknij polecenie **Konfiguruj odwołanie do usługi**.

3. W oknie dialogowym **Konfigurowanie odwołań do usługi** Usuń zaznaczenie pola wyboru **Użyj ponownie typów w przywoływanych zestawach** .

## <a name="related-topics"></a>Powiązane tematy

| Tytuł | Opis |
| - | - |
| [Przewodnik: tworzenie prostej usługi WCF w aplikacji Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | Zawiera pokaz krok po kroku dotyczące tworzenia i używania usług WCF w programie Visual Studio. |
| [Przewodnik: Tworzenie usługi danych programu WCF przy użyciu WPF i Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | Zawiera pokaz krok po kroku dotyczący sposobu tworzenia i używania WCF Data Services w programie Visual Studio. |
| [Korzystanie z narzędzi programistycznych WCF](/dotnet/framework/wcf/using-the-wcf-development-tools) | W tym artykule omówiono sposób tworzenia i testowania usług WCF w programie Visual Studio. |
| | [Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołania usługi danych programu WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [Rozwiązywanie problemów z odwołaniami do usługi](../data-tools/troubleshooting-service-references.md) | Przedstawia niektóre typowe błędy, które mogą wystąpić w odniesieniu do usług i sposobach ich zapobiegania. |
| [Debugowanie usług WCF](../debugger/debugging-wcf-services.md) | Opisuje typowe problemy z debugowaniem i techniki, które mogą wystąpić podczas debugowania usług WCF. |
| [Przewodnik: Tworzenie wielowarstwowej aplikacji danych](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | Zawiera instrukcje krok po kroku dotyczące tworzenia określonego zestawu danych i rozdzielania kodu TableAdapter i zestawu danych na wiele projektów. |
| [Konfigurowanie odwołania do usługi — okno dialogowe](../data-tools/configure-service-reference-dialog-box.md) | Opisuje elementy interfejsu użytkownika okna dialogowego **Konfigurowanie odwołania do usługi** . |

## <a name="reference"></a>Odwołanie

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>Zobacz też

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
