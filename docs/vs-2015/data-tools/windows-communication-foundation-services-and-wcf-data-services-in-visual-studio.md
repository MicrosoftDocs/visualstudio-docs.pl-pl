---
title: Usługi Windows Communication Foundation i usługi danych programu WCF
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c366ce44ab65ded62370dd3c219473089d5ca111
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299569"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio udostępnia narzędzia do pracy z usługami Windows Communication Foundation (WCF) i [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], technologii firmy Microsoft do tworzenia aplikacji rozproszonych. Ten temat zawiera wprowadzenie do usług z perspektywy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ej. Aby uzyskać pełną dokumentację, zobacz [Usługi danych programu WCF 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a).

## <a name="what-is-wcf"></a>Co to jest WCF?
 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] to ujednolicona platforma do tworzenia bezpiecznych, niezawodnych, transakcyjnych i międzyoperacyjnych aplikacji rozproszonych. Zastępuje starsze technologii komunikacji międzyprocesowej, takich jak usługi sieci Web ASMX, wywołaniem funkcji zdalnych .NET, usługi Enterprise (DCOM) i usługi MSMQ. Usługi WCF łączy funkcje tych technologii pod ujednolicony model programowania. Upraszcza to środowisko tworzenia aplikacji rozproszonej.

#### <a name="what-are-wcf-data-services"></a>Co to są usługi danych WCF
 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] to implementacja standardu protokołu Open Data (OData).  Usługi danych WCF umożliwia udostępnianie danych tabelarycznych jako zestaw interfejsów API REST, co pozwala zwracanych danych przy użyciu standardowych poleceń HTTP, takich jak pobieranie, POST, PUT lub usunąć. Po stronie serwera Usługi danych programu WCF są zastępowane przez [interfejs API sieci Web ASP.NET](https://dotnet.microsoft.com/apps/aspnet/apis) na potrzeby tworzenia nowych usług OData. Biblioteka klienta Usługi danych programu WCF nadal jest dobrym rozwiązaniem w przypadku korzystania z usług OData w aplikacji .NET z programu Visual Studio (**Project &#124; Dodaj odwołanie do usługi**). Aby uzyskać więcej informacji, zobacz [Usługi danych programu WCF 4,5](https://go.microsoft.com/fwlink/?LinkID=119952).

### <a name="wcf-programming-model"></a>Model programowania w programie WCF
 W modelu programowania usług WCF opiera się na komunikację między dwiema jednostkami: usługi WCF i klienta WCF. Model programowania jest hermetyzowany w przestrzeni nazw <xref:System.ServiceModel> w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

#### <a name="wcf-service"></a>Usługa WCF
 Usługa WCF opiera się na interfejs, który definiuje kontrakt między usługą i klienta. Jest on oznaczony atrybutem <xref:System.ServiceModel.ServiceContractAttribute>, jak pokazano w poniższym kodzie:

 [!code-csharp[WCFWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#6)]
 [!code-vb[WCFWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#6)]

 [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
 [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

 Definiujesz funkcje lub metody, które są uwidaczniane przez usługę WCF, oznaczając je atrybutem <xref:System.ServiceModel.OperationContractAttribute>. Ponadto można uwidocznić dane serializowane, zaznaczając typ złożony z atrybutem <xref:System.Runtime.Serialization.DataContractAttribute>. Umożliwia to powiązanie danych w kliencie.

 Po zdefiniowaniu interfejs i jego metod one są hermetyzowane w klasie, która implementuje interfejs. Jednej klasy usługi WCF można zaimplementować wiele kontraktów usług.

 Usługa WCF jest udostępniona do użycia na podstawie tego, co jest znane jako *punkt końcowy*. Punkt końcowy zapewnia jedynym sposobem, aby komunikować się z usługą; nie możesz uzyskać dostępu usługi za pośrednictwem odwołanie bezpośrednie tak jak w przypadku innych klas.

 Punkt końcowy składa się z adresu, powiązanie i kontrakt. Określa adres, gdzie znajduje się usługa; może to być adres URL, adresu FTP lub sieci lub ścieżkę lokalną. Powiązanie definiuje sposób komunikacji z usługą. Powiązania WCF zapewniają wszechstronny modelu do określania protokołów, takich jak HTTP lub FTP mechanizmu zabezpieczeń, takie jak uwierzytelnianie Windows lub nazwy użytkownika i hasła i wiele więcej. Kontrakt obejmuje operacje, które są udostępniane przez klasy usługi WCF.

 Wiele punktów końcowych mogą być udostępniane dla jednej usługi WCF. Dzięki temu różnych klientów do komunikowania się z tą samą usługą na różne sposoby. Na przykład usługi bankowe może zapewnia jeden punkt końcowy dla pracowników i inny dla klientów zewnętrznych przy użyciu innego adresu, powiązania i/lub kontraktu.

#### <a name="wcf-client"></a>Klienta programu WCF
 Klient WCF składa się z *serwera proxy* , który umożliwia aplikacji komunikację z usługą WCF oraz punkt końcowy, który jest zgodny z punktem końcowym zdefiniowanym dla usługi. Serwer proxy jest generowany po stronie klienta w pliku app.config i zawiera informacje na temat typów i metod, które są udostępniane przez usługę. W przypadku usług, które udostępniają wiele punktów końcowych klienta można wybrać jedną, która najlepiej pasuje do swoich potrzeb, na przykład do komunikowania się za pośrednictwem protokołu HTTP i korzystać z uwierzytelniania Windows.

 Po utworzeniu klienta programu WCF możesz odwoływać się usługi w kodzie tak samo jak każdy inny obiekt. Na przykład, aby wywołać metodę `GetData` pokazana wcześniej, należy napisać kod podobny do następującego:

 [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
 [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

## <a name="wcf-tools-in-visual-studio"></a>Narzędzia WCF w programie Visual Studio
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] udostępnia narzędzia, które ułatwiają tworzenie zarówno usług WCF, jak i klientów programu WCF. Aby zapoznać się z przewodnikiem, który demonstruje narzędzia, zobacz [Przewodnik: tworzenie prostej usługi WCF w Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="creating-and-testing-wcf-services"></a>Tworzenie i testowanie usług WCF
 Możesz użyć szablonów [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] WCF jako podstawy, aby szybko utworzyć własną usługę. Następnie służy hostów Auto usługi WCF i WCF przetestować klienta do debugowania i testowania tej usługi. Razem te narzędzia zapewniają szybki i wygodny debugowania i cyklu testowania i wyeliminować konieczność zaangażowani w zapewnienie modelu hostingu na wczesnym etapie.

#### <a name="wcf-templates"></a>Szablony programu WCF
 Szablony [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] WCF zapewniają podstawową strukturę klasy do tworzenia usług. Kilka szablonów WCF jest dostępnych w oknie dialogowym **Dodaj nowy projekt** . Należą do projektów biblioteki usługi WCF, witryn sieci Web usługi WCF i szablony elementów usług WCF.

 Po wybraniu szablonu, pliki zostaną dodane dla kontraktu usługi, implementacji usługi i konfigurację usługi. Wszystkie niezbędne atrybuty zostały już dodane, tworzenie prostego typu "Hello World", usługi i nie miał pisania kodu. Będzie oczywiście, chcesz dodać kod, aby zapewnić funkcji i metod usługi rzeczywistych, ale Szablony stanowią podstawę podstawowe.

 Aby dowiedzieć się więcej na temat szablonów usługi WCF, zobacz [szablony Visual Studio programu WCF](https://msdn.microsoft.com/library/6a608575-3535-4190-89da-911e24c8374f).

#### <a name="wcf-service-host"></a>Host usługi WCF
 Po uruchomieniu debugera [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (przez naciśnięcie klawisza F5) dla projektu usługi WCF narzędzie hosta usługi WCF zostanie automatycznie uruchomione, aby hostować usługę lokalnie. Host usługi WCF wylicza usługi w projekcie usługi WCF, ładuje tej konfiguracji projektu, a następnie tworzy wystąpienie hosta dla każdej usługi, które znajdzie.

 Za pomocą Host usługi WCF, możesz przetestować bez pisania dodatkowego kodu lub zatwierdzania do określonego hosta podczas tworzenia usługi WCF.

 Aby dowiedzieć się więcej na temat hosta usługi WCF, zobacz [host usługi WCF (WcfSvcHost. exe)](https://msdn.microsoft.com/library/8643a63d-a357-4c39-bd6c-cdfdf71e370e).

#### <a name="wcf-test-client"></a>Klient testowy WCF
 Narzędzia WCF przetestować klienta umożliwia badanie parametrów wejściowych, przesyłanie, że dane wejściowe do usługi WCF i wyświetlić odpowiedź, którą usługa wysyła z powrotem. Zapewnia wygodne usługi testowania środowisko podczas łączenia z hostem usługi WCF. Narzędzie można znaleźć w folderze \Common7\IDE, który dla programu Visual Studio 2015 został zainstalowany na dysku C:: **C:\Program Files (x86) \Microsoft Visual Studio 14.0 \ Common7\IDE\\** .

 Po naciśnięciu klawisza F5, aby debugować projekt usługi WCF, klient testowy WCF otwiera i wyświetla listę punktów końcowych usługi, które są zdefiniowane w pliku konfiguracji. Można przetestować parametrów i uruchom usługę i powtórz ten proces nieprzerwanie testować i weryfikować usługi.

 Aby dowiedzieć się więcej o kliencie testowym WCF, zobacz [klienta testowego WCF (WcfTestClient. exe)](https://msdn.microsoft.com/library/d4302855-677f-4640-aa90-c5d785d72fb7).

### <a name="accessing-wcf-services-in-visual-studio"></a>Dostęp do usług WCF w programie Visual Studio
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] upraszcza zadanie tworzenia klientów WCF, automatycznie generując serwer proxy i punkt końcowy dla usług, które można dodać przy użyciu okna dialogowego **Dodaj odwołanie do usługi** . Wszystkie informacje o konfiguracji niezbędne są dodawane do pliku app.config. Większość przypadków wszystko, co należy zrobić to utworzenia wystąpienia usługi do jej używania.

 Okno dialogowe **Dodaj odwołanie do usługi** umożliwia wprowadzenie adresu usługi lub wyszukanie usługi zdefiniowanej w rozwiązaniu. Okno dialogowe zwraca listę usług i operacje udostępniane przez te usługi. Umożliwia on również definiowanie przestrzeni nazw za pomocą którego można będzie odwoływać się do usługi w kodzie.

 Okno dialogowe **Konfigurowanie odwołań do usług** umożliwia dostosowanie konfiguracji usługi. Można zmienić adres usługi, określ poziom dostępu, zachowanie asynchroniczne i typy kontraktu komunikatu i konfigurować ponowne użycie typu.

## <a name="how-to-select-a-service-endpoint"></a>Porady: Wybieranie punktu końcowego usługi
 Niektóre usługi Windows Communication Foundation (WCF) ujawniają wiele punktów końcowych, za pomocą których klient może komunikować się z usługą. Na przykład usługa może narazić jeden punkt końcowy, który używa protokołu HTTP powiązanie i nazwę użytkownika / hasło zabezpieczeń i drugi punkt końcowy, który korzysta z protokołu FTP i uwierzytelniania Windows. Pierwszy punkt końcowy mogą być używane przez aplikacje uzyskujące dostęp do usługi z poza zaporą, podczas gdy drugi mogą być używane w sieci intranet.

 W takim przypadku można określić `endpointConfigurationName` jako parametr do konstruktora dla odwołania do usługi.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-select-a-service-endpoint"></a>Aby wybrać punkt końcowy usługi

1. Aby dodać odwołanie do usługi WCF, kliknij prawym przyciskiem myszy węzeł projektu w Eksplorator rozwiązań i wybierz polecenie **Dodaj odwołanie do usługi** .

2. W edytorze kodu Dodaj Konstruktor dla odwołania do usługi:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Zastąp wartość *ServiceReference* z przestrzenią nazw dla odwołania do usługi i Zastąp *Service1Client* nazwą usługi.

3. Zostanie wyświetlona lista IntelliSense za pomocą przeciążenia konstruktora. Wybierz Przeciążenie `endpointConfigurationName As String`.

4. Po przeciążeniu wpisz `=` *ConfigurationName*, gdzie *ConfigurationName* jest nazwą punktu końcowego, którego chcesz użyć.

    > [!NOTE]
    > Jeśli nie znasz nazwy dostępnych punktów końcowych, można je znaleźć w pliku app.config.

#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Aby znaleźć dostępne punkty końcowe dla usługi WCF

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik App. config dla projektu, który zawiera odwołanie do usługi, a następnie kliknij polecenie **Otwórz**. Plik pojawi się w edytorze kodu.

2. Wyszukaj tag `<Client>` w pliku.

3. Wyszukaj pod tagiem `<Client>` tagu, który rozpoczyna się od `<Endpoint>`.

     Jeśli odwołanie do usługi zawiera wiele punktów końcowych, będą dostępne co najmniej dwa Tagi `<Endpoint`.

4. Wewnątrz tagu `<EndPoint>` można znaleźć parametr `name="`*SomeService*`"` (gdzie *SomeService* reprezentuje nazwę punktu końcowego). Jest to nazwa punktu końcowego, który może zostać przesłany do `endpointConfigurationName As String` przeciążenie konstruktora dla odwołania do usługi.

## <a name="how-to-call-a-service-method-asynchronously"></a>Instrukcje: asynchroniczne wywoływanie metody usługi
 Większość metod w usług Windows Communication Foundation (WCF) może zostać wywołana synchronicznie lub asynchronicznie. Asynchroniczne wywołanie metody umożliwia aplikacji, aby kontynuować pracę, podczas gdy metoda jest wywoływana, gdy działa przez wolne połączenie.

 Domyślnie gdy odwołanie do usługi zostanie dodany do projektu go jest skonfigurowany do wywołania metod synchronicznie. Można zmienić zachowanie, aby wywołać metody asynchronicznie, zmieniając ustawienie w oknie dialogowym **Konfigurowanie odwołania do usługi** .

> [!NOTE]
> Ta opcja jest ustawiona na podstawie za daną usługę. Jeśli jedna metoda usługi nosi nazwę asynchronicznej, wszystkie metody musi zostać wywołana asynchronicznie.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-call-a-service-method-asynchronously"></a>Do wywołania metody usługi asynchronicznie

1. W **Eksplorator rozwiązań**wybierz odwołanie do usługi.

2. W menu **projekt** kliknij polecenie **Konfiguruj odwołanie do usługi**.

3. W oknie dialogowym **Konfigurowanie odwołania do usługi** zaznacz pole wyboru **Generuj operacje asynchroniczne** .

## <a name="how-to-bind-data-returned-by-a-service"></a>Porady: powiązywanie danych zwracanych przez usługę
 Można powiązać danych zwracanych przez usługę Windows Communication Foundation (WCF) do formantu, tak samo, jak dowolnego innego źródła danych można powiązać formant. Po dodaniu odwołania do usługi WCF, jeśli usługa zawiera złożone typy, które zwracają dane, są one automatycznie dodawane do okna **źródła danych** .

#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Aby powiązać formant jedno pole danych zwracane przez usługę WCF

1. W menu **dane** kliknij przycisk **Pokaż źródła danych**. Zostanie wyświetlone okno **źródła danych** .

2. W oknie **źródła danych** rozwiń węzeł odwołania do usługi. Zostaną wyświetlone wszystkie typy złożone zwracane przez usługę.

3. Rozwiń węzeł dla typu. Pojawi się pola danych dla tego typu.

4. Wybierz pole i kliknij strzałkę listy rozwijanej, aby wyświetlić listę elementów sterujących, które są dostępne dla typu danych.

5. Kliknij typ kontrolki, którą chcesz powiązać.

6. Przeciągnij pole do formularza. Kontrolka zostanie dodana do formularza ze składnikiem <xref:System.Windows.Forms.BindingSource> i składnikiem <xref:System.Windows.Forms.BindingNavigator>.

7. Powtórz kroki od 4, chociaż 6 dla innych pól, które chcesz powiązać.

#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Aby powiązać formant typu złożonego, zwracane przez usługę WCF

1. W menu **dane** wybierz pozycję **Pokaż źródła danych**. Zostanie wyświetlone okno **źródła danych** .

2. W oknie **źródła danych** rozwiń węzeł odwołania do usługi. Zostaną wyświetlone wszystkie typy złożone zwracane przez usługę.

3. Wybierz węzeł dla typu, a następnie kliknij strzałkę listy rozwijanej, aby wyświetlić listę dostępnych opcji.

4. Kliknij **formant DataGridView** , aby wyświetlić dane w siatce lub **szczegóły** , aby wyświetlić dane w poszczególnych kontrolkach.

5. Przeciągnij węzeł na formularzu. Kontrolki zostaną dodane do formularza wraz ze składnikiem <xref:System.Windows.Forms.BindingSource> i składnikiem <xref:System.Windows.Forms.BindingNavigator>.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Porady: Konfigurowanie usługi do ponownego użycia istniejących typów
 Po dodaniu do projektu odwołanie do usługi żadnych typów zdefiniowanych w usłudze są generowane w projekcie lokalnym. W wielu przypadkach tworzy zduplikowane typy, gdy usługa używa popularnych typów [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] lub gdy typy są zdefiniowane w bibliotece udostępnionej.

 Aby uniknąć tego problemu, typów w przywoływanych zestawach są udostępnione domyślnie. Jeśli chcesz wyłączyć udostępnianie typu dla jednego lub kilku zestawów, możesz to zrobić w oknie dialogowym **Konfigurowanie odwołań do usługi** .

#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Aby wyłączyć udostępnianie typu w jednym zestawie

1. W **Eksplorator rozwiązań**wybierz odwołanie do usługi.

2. W menu **projekt** kliknij polecenie **Konfiguruj odwołanie do usługi**.

3. W oknie dialogowym **Konfigurowanie odwołań do usług** wybierz pozycję **Użyj ponownie typów w określonych przywoływanych zestawach**.

4. Zaznacz pole wyboru dla każdego zestawu, w której chcesz włączyć udostępnianie typu. Aby wyłączyć udostępnianie dla zestawu typu, to pole wyboru zostanie wyczyszczone.

#### <a name="to-disable-type-sharing-in-all-assemblies"></a>Aby wyłączyć udostępnianie typu w wszystkie zestawy

1. W **Eksplorator rozwiązań**wybierz odwołanie do usługi.

2. W menu **projekt** kliknij polecenie **Konfiguruj odwołanie do usługi**.

3. W oknie dialogowym **Konfigurowanie odwołań do usługi** Usuń zaznaczenie pola wyboru **Użyj ponownie typów w przywoływanych zestawach** .

## <a name="related-topics"></a>Tematy pokrewne

|Stanowisko|Opis|
|-----------|-----------------|
|[Przewodnik: tworzenie prostej usługi WCF w aplikacji Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Zawiera pokaz krok po kroku dotyczące tworzenia i używania usług WCF w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Przewodnik: tworzenie usługi danych programu WCF za pomocą struktur WPF i Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Zawiera pokaz krok po kroku dotyczący sposobu tworzenia i używania [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Używanie narzędzi deweloperskich programu WCF](https://msdn.microsoft.com/library/054adb87-c244-4d5a-83d1-0b2b44bd454b)|W tym artykule omówiono sposób tworzenia i testowania usług WCF w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołania do usługi](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)|W tym artykule opisano, jak dodawanie, aktualizowanie lub usuwanie usługi WCF z projektu.|
|[Instrukcje: dodawanie, aktualizowanie lub usuwanie odwołań usługi danych WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|W tym artykule omówiono sposób odwoływania się do [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] i używania ich w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Rozwiązywanie problemów z odwołaniami usługi](../data-tools/troubleshooting-service-references.md)|Przedstawia informacje o typowych błędów, które mogą wystąpić, za pomocą odwołań do usług i sposobu zapobiegania im.|
|[Debugowanie usług WCF](../debugger/debugging-wcf-services.md)|Zawiera opis typowych problemów debugowania i technik, które mogą wystąpić podczas debugowania usług WCF.|
|[Omówienie usługi Windows Communication Foundation Authentication](https://msdn.microsoft.com/library/6e121a28-89e8-4974-88a8-70aaa6a7d52b)|Opisuje sposób używania usługi WCF do świadczenia usług roli dla witryny sieci Web.|
|[Przewodnik: tworzenie n-warstwowych aplikacji do obsługi danych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Instrukcje krok po kroku dotyczące tworzenia typizowany zestaw danych i oddzielenie kodu TableAdapter i zestaw danych do wielu projektów.|
|[Konfigurowanie odwołania do usługi, okno dialogowe](../data-tools/configure-service-reference-dialog-box.md)|Opisuje elementy interfejsu użytkownika okna dialogowego **Konfigurowanie odwołania do usługi** .|

## <a name="reference"></a>Tematy pomocy
 <xref:System.ServiceModel>

 <xref:System.Data.Services>

## <a name="see-also"></a>Zobacz też
 [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
