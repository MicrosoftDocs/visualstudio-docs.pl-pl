---
title: Dowiedz się, podstawy tworzenia aplikacji przy użyciu zestawu narzędzi Xamarin.Forms
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: bc7e46af7e29ef554b80bd9244910e0c67d373af
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299757"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Podstawowe informacje dotyczące tworzenia aplikacji za pomocą platformy Xamarin.Forms w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po wykonaniu kroków [Instalator i instalacja](../cross-platform/setup-and-install.md) i [Sprawdź swoje środowisko Xamarin](../cross-platform/verify-your-xamarin-environment.md), w tym instruktażu dowiesz się, jak utworzyć podstawową aplikację (pokazana poniżej), za pomocą zestawu narzędzi Xamarin.Forms. Za pomocą zestawu narzędzi Xamarin.Forms Ty napiszesz całości kodu interfejsu użytkownika raz w bibliotece klas przenośnych (PCL). Xamarin zostaną automatycznie renderowania natywne kontrolki interfejsu użytkownika dla systemów iOS, Android i Windows Platform. Zalecamy takie podejście, ponieważ opcja PCL najlepiej obsługuje przy użyciu tylko tych interfejsów API platformy .NET, które są obsługiwane na wszystkich platformach docelowych, a ponieważ zestawu narzędzi Xamarin.Forms umożliwia udostępnianie kodu interfejsu użytkownika różnych platformach.

 ![Przykład aplikacji pogody w systemach Android, iOS i Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

 Wykonasz te czynności na tworzenie:

- [Konfigurowanie rozwiązania programu](#solution)

- [Pisanie kodu usług udostępnionych danych](#dataservice)

- [Zacznij pisanie współdzielonym kodem interfejsu użytkownika](#uicode)

- [Przetestuj swoją aplikację przy użyciu programu Visual Studio Emulator for Android](#test)

- [Zakończ interfejsu użytkownika za pomocą natywnego wyglądu i działania na platformach](#finish)

> [!TIP]
> Możesz znaleźć pełnego kodu źródłowego dla tego projektu w [przykłady środowiska xamarin — formularze repozytorium w serwisie GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).

## <a name="solution"></a> Konfigurowanie rozwiązania programu
 Te kroki służą utworzeniu rozwiązanie Xamarin.Forms, zawierający PCL dla udostępnionego kodu i dwa dodano pakiety NuGet.

1. W programie Visual Studio Utwórz nowy **pusta aplikacja (Xamarin.Forms przenośna)** rozwiązania i nadaj mu nazwę **WeatherApp**. Można znaleźć ten szablon najłatwiej, wprowadzając **Xamarin.Forms** w polu wyszukiwania.

     Jeśli tak nie jest dostępne, może być konieczne instalacji Xamarin lub włączyć funkcję Visual Studio 2015, zobacz [Instalator i instalacja](../cross-platform/setup-and-install.md).

     ![Tworzenie nowego projektu platformy Xamarin &#40;. Forms dla aplikacji&#41; przenośnej](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

2. Po kliknięciu przycisku OK spowoduje utworzenie rozwiązania, będziesz mieć wiele pojedynczych projektów:

    - **WeatherApp (przenośna)** : PCL, gdzie Ty napiszesz kod, który jest współużytkowany przez platform, w tym wspólnej logiki biznesowej i kodu interfejsu użytkownika przy użyciu zestawu narzędzi Xamarin.Forms.

    - **WeatherApp.Droid**: projekt, który zawiera natywnego kodu dla systemu Android. To jest ustawiony jako domyślny projekt startowy.

    - **WeatherApp.iOS**: projekt, który zawiera kod natywny dla systemu iOS.

    - **WeatherApp.UWP**: projekt, który zawiera kod platformy uniwersalnej systemu Windows do systemu Windows 10.

    - **WeatherApp.Windows (Windows 8.1)** : projekt, który zawiera kod natywny Windows 8.1.

    - **WeatherApp.WinPhone (Windows Phone 8.1)** : projekt, który zawiera kod macierzysty Windows Phone.

    > [!NOTE]
    > Możesz usunąć wszystkie projekty, które nie są przeznaczone dla platformy. Na potrzeby tego przewodnika firma Microsoft będzie odwoływać się do projektów systemów Android, iOS i Windows Phone 8.1. Praca z platformy uniwersalnej systemu Windows i Windows 8.1 projektów jest bardzo podobny do pracy z projektu Windows Phone 8.1.

     W ramach każdego natywnego projektu mają dostęp do natywnych projektanta dla odpowiednich platform i zaimplementować platformy określonymi ekranami i funkcjonalność, zgodnie z potrzebami.

3. Uaktualnij pakiet Xamarin.Forms NuGet w rozwiązaniu do najnowszej stabilnej wersji w następujący sposób. Zaleca się takiego postępowania, zawsze podczas tworzenia nowego rozwiązania Xamarin:

    - Wybierz **Narzędzia > Menedżer pakietów NuGet > Zarządzaj pakietami NuGet dla rozwiązania**.

    - W obszarze **aktualizacje** karcie wyboru **Xamarin.Forms** aktualizacji i sprawdź, zaktualizuj wszystkie projekty w rozwiązaniu. (Uwaga: nie zaznaczaj żadnych aktualizacji dla Xamarin.Android.Support wyboru.)

    - Aktualizacja **wersji** pole **najnowszy stabilny** wersji, która jest dostępna.

    - Kliknij przycisk **aktualizacji**.

         ![Aktualizowanie pakietu NuGet Xamarin. Forms](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")

4. Dodaj **Newtonsoft.Json** i pakiet NuGet do projektu PCL, którego będziesz używać do przetwarzania informacji pobrane z usługi danych o pogodzie:

    - W Menedżera pakietów NuGet (wciąż otwarty z kroku 3), wybierz **Przeglądaj** kartę i wyszukaj **Newtonsoft**.

    - Wybierz **Newtonsoft.Json**.

    - Sprawdź **WeatherApp** projektu (jest to tylko projektu, w którym należy zainstalować pakiet).

    - Upewnij się, **wersji** pole jest ustawione na **najnowszy stabilny** wersji.

    - Kliknij przycisk **zainstalować**.

    - ![Lokalizowanie i instalowanie pakietu NuGet Newtonsoft. JSON](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

5. Powtórz krok 4, aby znaleźć i zainstalować **Microsoft.Net.Http** pakietu.

6. Skompiluj rozwiązanie i upewnij się, że żadne błędy kompilacji.

## <a name="dataservice"></a> Pisanie kodu usług udostępnionych danych
 **WeatherApp (przenośna)** projekt jest, gdzie Ty napiszesz kod dla biblioteki klas przenośnych (PCL), który jest udostępniany na wszystkich platformach. PCL jest automatycznie uwzględnione w aplikacji pakietów kompilacji przez system iOS, Android i Windows Phone projektów.

 Aby uruchomić ten przykład, najpierw musisz zarejestrować się uzyskać bezpłatny klucz interfejsu API w [ http://openweathermap.org/appid ](https://openweathermap.org/appid).

 Poniższe kroki następnie dodaj kod do aplikacji PCL dostęp do przechowywania danych pochodzących z tej usługi pogody:

1. Kliknij prawym przyciskiem myszy **WeatherApp** projektu, a następnie wybierz **Dodaj > klasa...** . W **Dodaj nowy element** okno dialogowe, nazwij plik **Weather.cs**. Ta klasa będzie używane do przechowywania danych z usługi danych o pogodzie.

2. Zastąp całą zawartość **Weather.cs** następującym kodem:

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

3. Dodaj klasę do projektu PCL o nazwie **DataService.cs** , w którym będziesz używać do przetwarzania danych JSON z usługi danych o pogodzie.

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

5. Dodaj klasę innych do PCL o nazwie **Core** którym zostanie umieszczony udostępnione logiki biznesowej, takich jak logiki, który wchodzi w skład ciąg zapytania z kod pocztowy, wywołuje usługę danych o pogodzie i wypełnia wystąpienie **pogody**klasy.

6. Zastąp zawartość **Core.cs** następującym kodem:

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

7. Tworzenie **WeatherApp** projektu PCL, aby upewnić się, kod jest poprawny.

## <a name="uicode"></a> Zacznij pisanie współdzielonym kodem interfejsu użytkownika
 Zestaw narzędzi Xamarin.Forms pozwalają na wdrożenie współdzielonym kodem interfejsu użytkownika w aplikacji PCL. W ramach tej procedury dodasz ekran do PCL z przyciskiem, którego aktualizacji jego tekstu przy użyciu danych zwracanych przez dane o pogodzie usługi kodu dodanego w poprzedniej sekcji:

1. Dodaj **stronę XAML formularzy** o nazwie **WeatherPage.cs** , klikając prawym przyciskiem myszy projekt **WeatherApp** i wybierając pozycję **Dodaj > nowy element.** ... W oknie dialogowym **Dodaj nowy element** Wyszukaj ciąg "formularze", wybierz **stronę XAML formularzy**i nadaj jej nazwę **WeatherPage.cs**.

     Zestaw narzędzi Xamarin.Forms jest oparte na XAML, więc tego kroku jest tworzony **WeatherPage.xaml** plików wraz z plikiem zagnieżdżonych związanym z kodem **WeatherPage.xaml.cs**. Dzięki temu można do generowania interfejsu użytkownika XAML lub kodu. Należy to zrobić część zarówno w tym przewodniku.

     ![Dodawanie nowej strony języka XAML platformy Xamarin. Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")

2. Aby dodać przycisk do ekranu WeatherPage, Zastąp zawartość WeatherPage.xaml następujących czynności:

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
           x:Class="WeatherApp.WeatherPage">
      <Button x:Name="getWeatherBtn" Text="Get Weather"/>
    </ContentPage>
    ```

     Należy zauważyć, że nazwa przycisku musi być zdefiniowany przy użyciu **x: Name** atrybutu, aby za pomocą nazwy z wewnątrz pliku związanego z kodem można odwoływać się tego przycisku.

3. Aby dodać program obsługi zdarzeń dla przycisku **kliknięciu** zdarzeń Aktualizowanie tekstu przycisku, Zastąp zawartość **WeatherPage.xaml.cs** z poniższym kodem. (Możesz zmienić "60601" inny kod pocztowy.)

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

4. Aby otworzyć **WeatherPage** jako pierwszy ekran po uruchomieniu aplikacji, Zamień Konstruktor domyślny w **App.cs** następującym kodem:

    ```csharp
    public App()
    {
        MainPage = new NavigationPage(new WeatherPage());
    }
    ```

5. Kompilacja projektu WeatherApp PCL, aby upewnić się, że kod jest poprawny.

## <a name="test"></a> Przetestuj swoją aplikację przy użyciu programu Visual Studio Emulator for Android
 Teraz można przystąpić do uruchomienia aplikacji! Uruchom tylko wersja systemu Android teraz sprawdzić, czy aplikacja jest pobieranie danych z usługi o pogodzie. Później należy również uruchomić z systemem iOS i Windows Phone wersji po dodaniu więcej elementów interfejsu użytkownika. (Uwaga: Jeśli korzystasz z programu Visual Studio, Windows 7, opłata wykonać te same czynności, ale zamiast tego zostanie programu Xamarin Player.)

1. Ustaw **WeatherApp.Droid** projekt jako projekt startowy, klikając go prawym przyciskiem myszy i wybierając polecenie **Ustaw jako projekt startowy**.

2. Na pasku narzędzi programu Visual Studio zobaczysz **WeatherApp.Droid** wymieniony jako projekt docelowy. Wybierz jedną z emulatorami systemu Android do debugowania i kliknę przycisk **F5**. Zalecamy użycie jednej z **emulatora VS** opcje, które uruchomi aplikację w Visual Studio Emulator for Android opcje.

     ![Wybieranie elementu docelowego debugowania emulatora programu VS](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")

3. Po uruchomieniu aplikacji w emulatorze, kliknij przycisk **uzyskać pogody** przycisku. Powinien zostać wyświetlony tekst przycisku zaktualizowana w celu **Chicago, IL**, czyli *tytuł* właściwości danych pobranych z usługi o pogodzie.

     ![Aplikacja pogody przed naciśnięciem przycisku](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")

## <a name="finish"></a> Zakończ interfejsu użytkownika za pomocą natywnego wyglądu i działania na platformach
 Zestaw narzędzi Xamarin.Forms renderuje natywne kontrolki interfejsu użytkownika dla każdej platformy, aby Twoja aplikacja ma automatycznie natywnego wyglądu i działania. Aby to zobaczyć więcej wyraźnie widać, teraz zakończyć interfejsu użytkownika za pomocą pola wejściowego dla kodu pocztowego, a następnie Wyświetl danych o pogodzie, który jest zwracany z usługi.

1. Zastąp zawartość **WeatherPage.xaml** z poniższym kodem. Należy pamiętać, że każdy element ma nazwę, za pomocą **x: Name** atrybutu zgodnie z wcześniejszym opisem, tak aby elementu odwołując się z kodu. Zestaw narzędzi Xamarin.Forms również udostępnia wiele [opcje układu](https://docs.microsoft.com/xamarin/xamarin-forms/user-interface/controls/layouts) (strony xamarin.com); w tym miejscu używa WeatherPage [StackLayout](https://docs.microsoft.com/dotnet/api/Xamarin.Forms.StackLayout?view=xamarin-forms) (strony xamarin.com).

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

    Zwróć uwagę na użycie **OnPlatform** tagu w interfejsie Xamarin.Forms. **OnPlatform** wybiera wartość właściwości, które są specyficzne dla bieżącej platformy, na którym uruchomiona jest aplikacja (zobacz [zewnętrznych składnia XAML](https://docs.microsoft.com/xamarin/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax) (strony xamarin.com). Firma Microsoft korzysta z jej w tym miejscu można ustawić inny kolor tekstu dla pól danych: biały w systemach Android i Windows Phone, Black w systemie iOS. Możesz użyć **OnPlatform** dla dowolnej właściwości i wszystkie typy danych korygowanie specyficzne dla platformy dowolne miejsce w Twojej XAML. W pliku związanym z kodem, można użyć [Device.OnPlatform API](https://docs.microsoft.com/xamarin/xamarin-forms/platform/device) w tym samym celu.

2. W **WeatherPage.xaml.cs**, Zastąp **GetWeatherBtn_Clicked** programu obsługi zdarzeń z poniższym kodem. Ten kod sprawdza, że nie jest kod pocztowy w polu wpisu, pobiera dane dla tego kodu pocztowego, ustawia kontekst powiązania cały ekran do wynikowego wystąpienia pogody, a następnie ustawia tekst przycisku "Wyszukaj ponownie." Należy pamiętać, że każdej etykiety w interfejsie użytkownika powiąże z właściwością klasy pogody, więc podczas równa kontekstu powiązania ekranu **pogody** wypadku te etykiety automatycznej aktualizacji.

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

3. Uruchom aplikację na wszystkich trzech platformach — Android, iOS i Windows Phone — przez kliknięcie prawym przyciskiem myszy odpowiedni projekt, wybierając opcję Ustaw jako projekt startowy i uruchamianie aplikacji na urządzeniu lub w emulatorem ani symulatorem. Wprowadź prawidłowy kod pocztowy Stanów Zjednoczonych (na przykład 60601), a następnie naciśnij przycisk Pobierz pogody, aby wyświetlić dane o pogodzie w danym regionie, jak pokazano poniżej. Oczywiście należy program Visual Studio podłączone do komputera z systemem Mac OS X w sieci dla projektu systemu iOS.

    ![Przykład aplikacji pogody w systemach Android, iOS i Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

   Trwa pełnego kodu źródłowego dla tego projektu [przykłady środowiska xamarin — formularze repozytorium w serwisie GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).
