---
title: Poznaj podstawy tworzenia aplikacji za pomocą platformy Xamarin. Forms
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 09da3bd59163cbef8b33b1d5ece732330e32eac7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918931"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Podstawowe informacje dotyczące tworzenia aplikacji za pomocą platformy Xamarin.Forms w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po wykonaniu kroków opisanych w [instalatorze i zainstalowaniu](../cross-platform/setup-and-install.md) i [zweryfikowaniu środowiska Xamarin](../cross-platform/verify-your-xamarin-environment.md)w tym przewodniku pokazano, jak utworzyć podstawową aplikację (pokazaną poniżej) za pomocą platformy Xamarin. Forms. Za pomocą platformy Xamarin. Forms napiszesz cały kod interfejsu użytkownika jeden raz w bibliotece klas przenośnych (PCL). Następnie program Xamarin automatycznie renderuje natywne kontrolki interfejsu użytkownika dla platform iOS, Android i Windows. Zalecamy takie podejście, ponieważ opcja PCL najlepiej obsługuje używanie tylko tych interfejsów API platformy .NET, które są obsługiwane na wszystkich platformach docelowych, a ponieważ Xamarin. Forms umożliwia udostępnianie kodu interfejsu użytkownika między platformami.

 ![Przykład aplikacji pogody w systemach Android, iOS i Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

 Wykonaj te czynności, aby je skompilować:

- [Konfigurowanie rozwiązania](#solution)

- [Zapisz kod usługi danych udostępnionych](#dataservice)

- [Rozpocznij pisanie udostępnionego kodu interfejsu użytkownika](#uicode)

- [Testowanie aplikacji przy użyciu emulatora programu Visual Studio dla systemu Android](#test)

- [Zakończ interfejs użytkownika, korzystając z natywnego wyglądu i działania na wielu platformach](#finish)

> [!TIP]
> Pełny kod źródłowy tego projektu można znaleźć w [repozytorium Xamarin-Forms-Samples w witrynie GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).

## <a name="set-up-your-solution"></a><a name="solution"></a> Konfigurowanie rozwiązania
 Te kroki tworzą rozwiązanie Xamarin. Forms zawierające kod w języku PCL dla kodu udostępnionego i dwa dodane pakiety NuGet.

1. W programie Visual Studio Utwórz nową **aplikację pustą (Xamarin. Forms Portable)** i nadaj jej nazwę **WeatherApp**. Ten szablon można łatwo znaleźć, wpisując **Xamarin. Forms** w polu wyszukiwania.

     Jeśli tak nie jest, może być konieczne zainstalowanie platformy Xamarin lub włączenie funkcji programu Visual Studio 2015, zobacz [Instalacja i instalacja](../cross-platform/setup-and-install.md).

     ![Tworzenie nowej pustej aplikacji &#40;platformy Xamarin. Forms Portable&#41; Project](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

2. Po kliknięciu przycisku OK w celu utworzenia rozwiązania będziesz mieć wiele indywidualnych projektów:

    - **WeatherApp (przenośny)**: PCL, w której będziesz pisać kod, który jest współużytkowany na różnych platformach, w tym typowej logiki biznesowej i kodu interfejsu użytkownika przy użyciu programu Xamarin. Forms.

    - **WeatherApp. Droid**: projekt, który zawiera natywny kod systemu Android. Ta wartość jest ustawiana jako domyślny projekt startowy.

    - **WeatherApp. iOS**: projekt zawierający natywny kod systemu iOS.

    - **WeatherApp. platformy UWP**: projekt zawierający kod platformy UWP systemu Windows 10.

    - **WeatherApp. Windows (Windows 8.1)**: projekt, który zawiera kod natywny Windows 8.1.

    - **WeatherApp. WinPhone (Windows Phone 8,1)**: projekt zawierający kod natywnej Windows Phone.

    > [!NOTE]
    > Możesz usunąć wszystkie projekty dla platformy, która nie jest celem. Na potrzeby tego instruktażu będziemy odwoływać się do projektów systemu Android, iOS i Windows Phone 8,1. Praca z projektami platformy UWP i Windows 8.1 jest bardzo podobna do pracy z projektem Windows Phone 8,1.

     W każdym projekcie macierzystym masz dostęp do projektanta natywnego dla odpowiedniej platformy i w razie potrzeby może zaimplementować ekrany i funkcje specyficzne dla platformy.

3. Uaktualnij pakiet NuGet programu Xamarin. Forms w rozwiązaniu do najnowszej stabilnej wersji w następujący sposób. Zalecamy to za każdym razem, gdy utworzysz nowe rozwiązanie Xamarin:

    - Wybierz pozycję **narzędzia > Menedżer pakietów nuget > Zarządzaj pakietami NuGet dla rozwiązania**.

    - Na karcie **aktualizacje** Sprawdź pozycję **Xamarin. Forms** Update i sprawdź, aby zaktualizować wszystkie projekty w rozwiązaniu. (Uwaga: pozostaw wszystkie aktualizacje dla platformy Xamarin. Android. obsługa nie jest zaznaczona).

    - Zaktualizuj pole **wersja** do **najnowszej** dostępnej wersji.

    - Kliknij przycisk **Update** (Aktualizuj).

         ![Aktualizowanie pakietu NuGet Xamarin. Forms](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")

4. Dodaj **Newtonsoft.Js** i pakiet NuGet do projektu PCL, który będzie używany do przetwarzania informacji pobranych z usługi danych pogody:

    - W Menedżerze pakietów NuGet (nadal otwarte z kroku 3) wybierz kartę **Przeglądaj** i wyszukaj ciąg **Newtonsoft**.

    - Wybierz **Newtonsoft.Js**.

    - Sprawdź projekt **WeatherApp** (jest to jedyny projekt, w którym należy zainstalować pakiet).

    - Upewnij się, że w polu **wersja** jest ustawiona **Najnowsza stabilna** wersja.

    - Kliknij przycisk **Zainstaluj**.

    - ![Lokalizowanie i Instalowanie Newtonsoft.Jsw pakiecie NuGet](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

5. Powtórz krok 4, aby znaleźć i zainstalować pakiet **Microsoft.NET. http** .

6. Skompiluj rozwiązanie i sprawdź, czy nie występują błędy kompilacji.

## <a name="write-shared-data-service-code"></a><a name="dataservice"></a> Zapisz kod usługi danych udostępnionych
 Projekt **WeatherApp (przenośny)** polega na tym, że napiszesz kod dla biblioteki klas przenośnych (PCL), która jest udostępniana na wszystkich platformach. PCL jest automatycznie dołączany do kompilacji pakietów aplikacji przez projekty systemu iOS, Android i Windows Phone.

 Aby uruchomić ten przykład, należy najpierw zarejestrować się w celu uzyskania bezpłatnego klucza interfejsu API pod adresem [http://openweathermap.org/appid](https://openweathermap.org/appid) .

 Poniższe kroki umożliwiają dodanie kodu do PCL w celu uzyskania dostępu i zapisania danych z tej usługi Pogoda:

1. Kliknij prawym przyciskiem myszy projekt **WeatherApp** i wybierz polecenie **Dodaj klasę >...**. W oknie dialogowym **Dodaj nowy element** nazwij plik **Weather.cs**. Ta klasa zostanie użyta do przechowywania danych z usługi danych pogody.

2. Zastąp całą zawartość **Weather.cs** poniższymi:

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            public string Title { get; set; }
            public string Temperature { get; set; }
            public string Wind { get; set; }
            public string Humidity { get; set; }
            public string Visibility { get; set; }
            public string Sunrise { get; set; }
            public string Sunset { get; set; }

            public Weather()
            {
                //Because labels bind to these values, set them to an empty string to
                //ensure that the label appears on all platforms by default.
                this.Title = " ";
                this.Temperature = " ";
                this.Wind = " ";
                this.Humidity = " ";
                this.Visibility = " ";
                this.Sunrise = " ";
                this.Sunset = " ";
            }
        }
    }
    ```

3. Dodaj kolejną klasę do projektu PCL o nazwie **DataService.cs** , w którym będziesz używać do przetwarzania danych JSON z usługi danych pogody.

4. Zastąp całą zawartość **DataService.cs** następującym kodem:

    ```csharp
    using System.Threading.Tasks;
    using Newtonsoft.Json;
    using System.Net.Http;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> getDataFromService(string queryString)
            {
                HttpClient client = new HttpClient();
                var response = await client.GetAsync(queryString);

                dynamic data = null;
                if (response != null)
                {
                    string json = response.Content.ReadAsStringAsync().Result;
                    data = JsonConvert.DeserializeObject(json);
                }

                return data;
            }
        }
    }
    ```

5. Dodaj trzecią klasę do pliku PCL o nazwie **Core** , w której umieścisz wspólną logikę biznesową, taką jak logika, która tworzy ciąg zapytania z kodem pocztowym, wywołuje usługę danych pogody i wypełnia wystąpienie klasy **Pogoda** .

6. Zastąp zawartość **Core.cs** poniższymi:

    ```csharp
    using System;
    using System.Threading.Tasks;

    namespace WeatherApp
    {
        public class Core
        {
            public static async Task<Weather> GetWeather(string zipCode)
            {
                //Sign up for a free API key at http://openweathermap.org/appid
                string key = "YOUR KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);

                if (results["weather"] != null)
                {
                    Weather weather = new Weather();
                    weather.Title = (string)results["name"];
                    weather.Temperature = (string)results["main"]["temp"] + " F";
                    weather.Wind = (string)results["wind"]["speed"] + " mph";
                    weather.Humidity = (string)results["main"]["humidity"] + " %";
                    weather.Visibility = (string)results["weather"][0]["main"];

                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);
                    weather.Sunrise = sunrise.ToString() + " UTC";
                    weather.Sunset = sunset.ToString() + " UTC";
                    return weather;
                }
                else
                {
                    return null;
                }
            }
        }
    }
    ```

7. Skompiluj projekt **WeatherApp** PCL, aby upewnić się, że kod jest poprawny.

## <a name="begin-writing-shared-ui-code"></a><a name="uicode"></a> Rozpocznij pisanie udostępnionego kodu interfejsu użytkownika
 Środowisko Xamarin. Forms pozwala zaimplementować współużytkowany kod interfejsu użytkownika w PCL. W tych krokach dodasz ekran do PCL z przyciskiem, który aktualizuje tekst z danymi zwróconymi przez kod usługi danych pogody dodany w poprzedniej sekcji:

1. Dodaj **stronę XAML formularzy** o nazwie **WeatherPage.cs** , klikając prawym przyciskiem myszy projekt **WeatherApp** i wybierając pozycję **Dodaj > nowy element.**... W oknie dialogowym **Dodaj nowy element** Wyszukaj ciąg "formularze", wybierz **stronę XAML formularzy**i nadaj jej nazwę **WeatherPage.cs**.

     Platforma Xamarin. Forms jest oparta na języku XAML, więc w tym kroku tworzony jest plik **WeatherPage. XAML** wraz z zagnieżdżonym plikiem związanym z kodem **WeatherPage.XAML.cs**. Pozwala to na generowanie interfejsu użytkownika za pomocą kodu XAML lub Code. W tym instruktażu wykonasz niektóre z tych czynności.

     ![Dodawanie nowej strony języka XAML platformy Xamarin. Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")

2. Aby dodać przycisk do ekranu WeatherPage, Zastąp zawartość pliku WeatherPage. XAML następującym:

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
           x:Class="WeatherApp.WeatherPage">
      <Button x:Name="getWeatherBtn" Text="Get Weather"/>
    </ContentPage>
    ```

     Należy zauważyć, że nazwa przycisku musi być zdefiniowana przy użyciu atrybutu **x:Name** , aby można było odwołać się do tego przycisku według nazwy z pliku związanego z kodem.

3. Aby dodać procedurę obsługi zdarzeń dla **klikniętego** zdarzenia przycisku w celu zaktualizowania tekstu przycisku, Zastąp zawartość **WeatherPage.XAML.cs** poniższym kodem. (Możesz zmienić "60601" na inny kod pocztowy).

    ```csharp
    using System;
    using Xamarin.Forms;

    namespace WeatherApp
    {
        public partial class WeatherPage: ContentPage
        {
            public WeatherPage()
            {
                InitializeComponent();
                this.Title = "Sample Weather App";
                getWeatherBtn.Clicked += GetWeatherBtn_Clicked;

                //Set the default binding to a default object for now
                this.BindingContext = new Weather();
            }

            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
            {
                Weather weather = await Core.GetWeather("60601");
                getWeatherBtn.Text = weather.Title;
            }
        }
    }
    ```

4. Aby otworzyć **WeatherPage** jako pierwszy ekran podczas uruchamiania aplikacji, Zastąp Konstruktor domyślny w **App.cs** następującym kodem:

    ```csharp
    public App()
    {
        MainPage = new NavigationPage(new WeatherPage());
    }
    ```

5. Skompiluj projekt WeatherApp PCL, aby upewnić się, że kod jest poprawny.

## <a name="test-your-app-using-the-visual-studio-emulator-for-android"></a><a name="test"></a> Testowanie aplikacji przy użyciu emulatora programu Visual Studio dla systemu Android
 Teraz wszystko jest gotowe do uruchomienia aplikacji. Uruchommy teraz tylko wersję systemu Android, aby sprawdzić, czy aplikacja pobiera dane z usługi Pogoda. Po dodaniu większej liczby elementów interfejsu użytkownika w późniejszym czasie zostanie również uruchomiony system iOS i Windows Phone wersje. (Uwaga: Jeśli korzystasz z programu Visual Studio w systemie Windows 7, wykonaj te same czynności, ale zamiast tego zostanie wyświetlony program Xamarin Player).

1. Ustaw projekt **WeatherApp. Droid** jako projekt startowy, klikając go prawym przyciskiem myszy i wybierając pozycję **Ustaw jako projekt startowy**.

2. Na pasku narzędzi programu Visual Studio zobaczysz **WeatherApp. Droid** na liście jako projekt docelowy. Wybierz jeden z emulatorów systemu Android na potrzeby debugowania i naciśnij klawisz **F5**. Zalecamy korzystanie z jednej z opcji **emulatora programu vs** , które będą uruchamiać aplikację w emulatorze programu Visual Studio dla opcji systemu Android.

     ![Wybieranie elementu docelowego debugowania emulatora programu VS](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")

3. Po uruchomieniu aplikacji w emulatorze kliknij przycisk **Pobierz Pogoda** . Powinien zostać wyświetlony tekst przycisku zaktualizowany do **Chicago, Il**, czyli Właściwość *tytułu* danych pobranych z usługi Pogoda.

     ![Aplikacja pogody przed naciśnięciem przycisku](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")

## <a name="finish-the-ui-with-a-native-look-and-feel-across-platforms"></a><a name="finish"></a> Zakończ interfejs użytkownika, korzystając z natywnego wyglądu i działania na wielu platformach
 Środowisko Xamarin. Forms renderuje natywne kontrolki interfejsu użytkownika dla każdej platformy, dzięki czemu aplikacja automatycznie ma natywny wygląd i działanie. Aby to dokładniej zobaczyć, Zakończ interfejs użytkownika przy użyciu pola wejściowego dla kodu pocztowego, a następnie Wyświetl dane pogodowe zwrócone przez usługę.

1. Zastąp zawartość **WeatherPage. XAML** poniższym kodem. Należy zauważyć, że każdy element ma nazwę przy użyciu atrybutu **x:Name** , zgodnie z wcześniejszym opisem, aby można było odwoływać się do elementu z kodu. Program Xamarin. Forms udostępnia również różne [Opcje układu](/xamarin/xamarin-forms/user-interface/controls/layouts) (Xamarin.com); w tym miejscu WeatherPage korzysta z [StackLayout](/dotnet/api/Xamarin.Forms.StackLayout?view=xamarin-forms) (Xamarin.com).

   ```xaml
   <?xml version="1.0" encoding="utf-8" ?>
   <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
          xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
          x:Class="WeatherApp.WeatherPage">

     <ContentPage.Resources>
       <ResourceDictionary>
         <Style x:Key="labelStyle" TargetType="Label">
           <Setter Property="TextColor" Value="#a8a8a8" />
           <Setter Property="FontSize" Value="Small" />
         </Style>
         <Style x:Key="fieldStyle" TargetType="Label">
           <Setter Property="TextColor">
             <OnPlatform x:TypeArguments="Color" iOS="Black" Android="White" WinPhone="White" />
           </Setter>
           <Setter Property="FontSize" Value="Medium" />
         </Style>
         <Style x:Key="fieldView" TargetType="ContentView">
           <Setter Property="Padding" Value="10,0,0,0" />
         </Style>
       </ResourceDictionary>
     </ContentPage.Resources>

     <ContentPage.Content>
       <ScrollView>
         <StackLayout>
           <StackLayout Orientation="Horizontal" HorizontalOptions="FillAndExpand"
                 BackgroundColor="#545454">
             <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
               <Label Text="Search by Zip Code" TextColor="White" FontAttributes="Bold"
                   FontSize="Medium" />
               <Label x:Name="zipCodeLabel" Text="Zip Code" Style="{StaticResource labelStyle}" />
               <Entry x:Name="zipCodeEntry" />
             </StackLayout>
             <StackLayout Padding="0,0,0,10" VerticalOptions="End">
               <Button x:Name="getWeatherBtn" Text="Get Weather" WidthRequest="185" BorderWidth="1" >
                 <!-- Set iOS colors; use defaults on other platforms -->
                 <Button.TextColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.TextColor>
                 <Button.BorderColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.BorderColor>
               </Button>
             </StackLayout>
           </StackLayout>
           <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
             <Label Text="Location" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Temperature" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="tempLabel" Text="{Binding Temperature}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="windLabel" Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Humidity" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="humidityLabel" Text="{Binding Humidity}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Visibility" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="visibilitylabel" Text="{Binding Visibility}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunriseLabel" Text="{Binding Sunrise}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunsetLabel" Text="{Binding Sunset}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
           </StackLayout>
         </StackLayout>
       </ScrollView>
     </ContentPage.Content>
   </ContentPage>
   ```

    Zwróć uwagę na użycie znacznika **onplatform** w oprogramowaniu Xamarin. Forms. **Platforma onplatform** wybiera wartość właściwości, która jest specyficzna dla bieżącej platformy, na której działa aplikacja (patrz [zewnętrzna składnia XAML](/xamarin/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax) (Xamarin.com). Używamy go tutaj, aby ustawić inny kolor tekstu dla pól danych: biały na urządzeniach z systemem Android i Windows Phone, czarny w systemie iOS. Możesz użyć **onplatform** dla każdej właściwości i dowolnego typu danych, aby wprowadzać korekty specyficzne dla platformy w dowolnym miejscu w języku XAML. W pliku związanym z kodem można użyć [interfejsu API Device. Onplatform](/xamarin/xamarin-forms/platform/device) w tym samym celu.

2. W **WeatherPage.XAML.cs**Zastąp procedurę obsługi zdarzeń **GetWeatherBtn_Clicked** poniższym kodem. Ten kod sprawdza, czy w polu wpis znajduje się kod pocztowy, pobiera dane dla tego kodu zip, ustawia kontekst powiązania całego ekranu z wynikiem wystąpienia pogody, a następnie ustawia tekst przycisku na "Wyszukaj ponownie". Należy zauważyć, że każda etykieta w interfejsie użytkownika wiąże się z właściwością klasy Pogoda, więc w przypadku ustawienia kontekstu powiązania ekranu do wystąpienia **pogody** te etykiety są aktualizowane automatycznie.

   ```csharp
   private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
   {
       if (!String.IsNullOrEmpty(zipCodeEntry.Text))
       {
           Weather weather = await Core.GetWeather(zipCodeEntry.Text);
           this.BindingContext = weather;
           getWeatherBtn.Text = "Search Again";
       }
   }
   ```

3. Uruchom aplikację na wszystkich trzech platformach (Android, iOS i Windows Phone), klikając prawym przyciskiem myszy odpowiedni projekt, wybierając pozycję Ustaw jako projekt startowy, a następnie uruchamiając aplikację na urządzeniu lub w emulatorze lub symulatorze. Wprowadź prawidłowy kod pocztowy Stany Zjednoczone (na przykład 60601) i naciśnij przycisk Get Pogoda, aby wyświetlić dane pogodowe dla tego regionu, jak pokazano poniżej. Konieczne będzie posiadanie programu Visual Studio połączonego z komputerem Mac OS X w sieci dla projektu systemu iOS.

    ![Przykład aplikacji pogody w systemach Android, iOS i Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

   Pełny kod źródłowy tego projektu znajduje się w [repozytorium Xamarin-Forms-Samples w witrynie GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).
