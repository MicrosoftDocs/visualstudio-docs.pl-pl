---
title: Tworzenie prostej aplikacji danych przy użyciu pakietu ADO.NET | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
caps.latest.revision: 46
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 19c20241914001f7095e63e0cc25f91b2ab5c35e
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664219"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Tworzenie prostej aplikacji danych przy użyciu pakietu ADO.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy tworzysz aplikację, która manipuluje danymi w bazie danych, wykonujesz podstawowe zadania, takie definiowania ciągów połączeń, wstawiania danych i uruchamianie przechowywanych procedur. Korzystając z tego tematu, można wykryć, jak korzystać z bazy danych z w ramach prostą aplikację "formularzy nad danymi" Windows Forms przy użyciu języka Visual C# lub Visual Basic i ADO.NET.  Wszystkie technologie danych .NET — w tym zestawy danych, LINQ to SQL i Entity Framework — ostatecznie wykonaj kroki, które są bardzo podobne do tych przedstawione w tym artykule.  
  
 W tym artykule przedstawiono prosty sposób pobrać dane z bazy danych w sposób bardzo szybko. Jeśli aplikacja musi modyfikować dane w sposób nietrywialnymi i aktualizują bazę danych, należy rozważyć używający narzędzia Entity Framework i korzystanie z danych powiązywanie kontrolek interfejsu użytkownika na zmiany w danych bazowych są synchronizowane automatycznie.  
  
> [!IMPORTANT]
>  W celu uproszczenia kodu nie zawiera obsługi wyjątków gotowych do produkcji.  
  
 **W tym temacie**  
  
-   [Konfigurowanie przykładowej bazy danych](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)  
  
-   [Tworzenie formularzy i dodawanie formantów](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)  
  
-   [Store parametry połączenia](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)  
  
-   [Pobieranie parametrów połączenia](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)  
  
-   [Pisanie kodu dla formularzy](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)  
  
-   [Testowanie aplikacji](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby utworzyć aplikację, będą potrzebne:  
  
- Visual Studio Community Edition.  
  
- SQL Server Express LocalDB.  
  
- Mała przykładowa baza danych, którą tworzysz, wykonując kroki opisane w [utworzyć bazę danych SQL za pomocą skryptu](../data-tools/create-a-sql-database-by-using-a-script.md).  
  
- Parametry połączenia dla bazy danych po jej skonfigurowaniu. Możesz znaleźć tę wartość otwierając **Eksplorator obiektów SQL Server**, otwierając menu skrótów dla bazy danych, wybierając **właściwości**i przewijając do **ConnectionString** właściwości.  
  
  W tym temacie założono, że znasz podstawowe funkcje środowiska IDE programu Visual Studio i można utworzyć aplikacji Windows Forms, dodawać formularze do tego projektu, umieszczać przyciski i inne kontrolki na tych formularzach, ustawiać właściwości tych kontrolek i kodować proste zdarzenia . Jeśli nie masz doświadczenia z tych zadań, zalecamy wykonanie [wprowadzenie do języka Visual C# i Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) przed rozpoczęciem tego tematu.  
  
##  <a name="BKMK_setupthesampledatabase"></a> Konfigurowanie przykładowej bazy danych  
 Przykładowa baza danych, w tym przewodniku składa się z tabel klienta i zamówień. Tabele nie zawierają początkowo żadnych danych, ale zostaną one dodane po uruchomieniu aplikacji, który utworzysz. Baza danych zawiera także pięć prostych przechowywanych procedur. [Tworzenie bazy danych SQL za pomocą skryptu](../data-tools/create-a-sql-database-by-using-a-script.md) zawiera skrypt języka Transact-SQL, który tworzy tabele, główne i obce klucze, ograniczenia i procedur składowanych.  
  
##  <a name="BKMK_createtheformsandaddcontrols"></a> Tworzenie formularzy i dodawanie formantów  
  
1. Utwórz projekt dla aplikacji Windows Forms, a następnie nadaj mu nazwę SimpleDataApp.  
  
    Program Visual Studio tworzy projekt i kilka plików, w tym pusty formularz Windows, który nosi nazwę Form1.  
  
2. Dodaj dwie formy Windows do projektu tak, że ma trzy formy, a następnie nadaj im następujące nazwy:  
  
   -   Nawigacja  
  
   -   NewCustomer  
  
   -   FillOrCancel  
  
3. Dla każdego formularza należy dodać pola tekstowe, przyciski i inne formanty, które pojawiają się na poniższych ilustracjach. Dla każdego formantu należy ustawić właściwości opisywane przez tabele.  
  
   > [!NOTE]
   >  Formanty etykiety i pole grupy zwiększają przejrzystość, ale nie są używane w kodzie.  
  
   **Formularz nawigacji**  
  
   ![Okno dialogowe nawigacji](../data-tools/media/simpleappnav.png "SimpleAppNav")  
  
|Formanty formularza nawigacji|Właściwości|  
|--------------------------------------|----------------|  
|Przycisk|Nazwa = btnGoToAdd|  
|Przycisk|Name = btnGoToFillOrCancel|  
|Przycisk|Nazwa = btnExit|  
  
 **Formularz NewCustomer**  
  
 ![Dodawanie nowego klienta i złożyć zamówienie](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")  
  
|Formanty formularza NewCustomer|Właściwości|  
|---------------------------------------|----------------|  
|TextBox|Nazwa = txtCustomerName|  
|TextBox|Nazwa = txtCustomerID<br /><br /> ReadOnly = PRAWDA|  
|Przycisk|Nazwa = btnCreateAccount|  
|NumericUpdown|MiejscaDziesiętne = 0<br /><br /> Maksymalna = 5000<br /><br /> Nazwa = numOrderAmount|  
|DateTimePicker|Format = krótki<br /><br /> Nazwa = dtpOrderDate|  
|Przycisk|Nazwa = btnPlaceOrder|  
|Przycisk|Nazwa = btnAddAnotherAccount|  
|Przycisk|Nazwa = btnAddFinish|  
  
 **Formularz FillOrCancel**  
  
 ![Wypełnij lub Anuluj zamówienia](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")  
  
|Formanty formularza FillOrCancel|Właściwości|  
|----------------------------------------|----------------|  
|TextBox|Nazwa = txtOrderID|  
|Przycisk|Nazwa = btnFindByOrderID|  
|DateTimePicker|Format = krótki<br /><br /> Nazwa = dtpFillDate|  
|DataGridView|Nazwa = dgvCustomerOrders<br /><br /> ReadOnly = PRAWDA<br /><br /> RowHeadersVisible = False|  
|Przycisk|Nazwa = btnCancelOrder|  
|Przycisk|Nazwa = btnFillOrder|  
|Przycisk|Nazwa = btnFinishUpdates|  
  
##  <a name="BKMK_storetheconnectionstring"></a> Store parametry połączenia  
 Gdy Twoja aplikacja próbuje otworzyć połączenie z bazą danych, aplikacja musi mieć dostęp do parametrów połączenia. Aby uniknąć wpisywania ciągu ręcznie w każdym formularzu, Przechowaj ciąg w pliku konfiguracji aplikacji w projekcie i Utwórz metodę, która zwraca ciąg, gdy metoda jest wywoływana z jakiegokolwiek formularza w aplikacji.  
  
 Można znaleźć w ciągu połączenia **Eksplorator obiektów SQL Server** przez kliknięcie prawym przyciskiem myszy bazę danych, wybierając **właściwości**, a następnie wyszukiwanie właściwości ConnectionString. Użyj klawiszy Ctrl + A, aby wybrać ten ciąg.  
  
1.  W **Eksploratora rozwiązań**, wybierz opcję **właściwości** węzeł w węźle projektu, a następnie wybierz **Settings.settings**.  
  
2.  W **nazwa** kolumny, wprowadź `connString`.  
  
3.  W **typu** listy wybierz **(parametry połączenia)**.  
  
4.  W **zakres** listy wybierz **aplikacji**.  
  
5.  W **wartość** kolumny, wprowadź parametry połączenia (bez żadnego poza cudzysłowy), a następnie zapisz zmiany.  
  
> [!NOTE]
>  W rzeczywistej aplikacji, należy przechowywać parametry połączenia bezpieczne, zgodnie z opisem w [parametry połączenia i pliki konfiguracyjne](http://msdn.microsoft.com/library/37df2641-661e-407a-a3fb-7bf9540f01e8).  
  
##  <a name="BKMK_retrievetheconnectionstring"></a> Pobieranie parametrów połączenia  
  
1.  Na pasku menu wybierz **projektu** > **Dodaj odwołanie**, a następnie dodaj odwołanie do System.Configuration.dll.  
  
2.  Na pasku menu wybierz **projektu** > **Dodaj klasę** można dodać plik klasy do projektu, a następnie Nazwij plik `Utility`.  
  
     Visual Studio tworzy plik i wyświetla go w **Eksploratora rozwiązań**.  
  
3.  W pliku narzędzie Zastąp kod symbolu zastępczego następującym kodem. Należy zauważyć ponumerowane komentarze (z prefiksem Util-), które identyfikują sekcje kodu. Tabela poniżej kod wywołuje punkty kluczowe.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.Threading.Tasks;  
    //Util-1 More namespaces.  
    using System.Configuration;   
  
    namespace SimpleDataApp  
    {  
        internal class Utility  
        {  
  
            //Get the connection string from App config file.  
            internal static string GetConnectionString()  
            {  
                //Util-2 Assume failure.  
                string returnValue = null;  
  
                //Util-3 Look for the name in the connectionStrings section.  
                ConnectionStringSettings settings =  
                ConfigurationManager.ConnectionStrings["SimpleDataApp.Properties.Settings.connString"];  
  
                //If found, return the connection string.  
                if (settings != null)  
                    returnValue = settings.ConnectionString;  
  
                return returnValue;  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.Linq  
    Imports System.Text  
    Imports System.Threading.Tasks  
    ' Util-1 More namespaces.  
    Imports System.Configuration  
  
    Namespace SimpleDataApp  
        Friend Class Utility  
  
            ' Get connection string from App config file.  
            Friend Shared Function GetConnectionString() As String  
  
                ' Util-2 Assume failure.  
                Dim returnValue As String = Nothing  
  
                ' Util-3 Look for the name in the connectionStrings section.  
                Dim settings As ConnectionStringSettings = ConfigurationManager.ConnectionStrings("SimpleDataApp.My.MySettings.connString")  
  
                ' If found, return the connection string.  
                If settings IsNot Nothing Then  
                    returnValue = settings.ConnectionString  
                End If  
  
                Return returnValue  
            End Function  
        End Class  
    End Namespace  
    ```  
  
    |Komentarz|Opis|  
    |-------------|-----------------|  
    |Util-1|Dodaj `System.Configuration` przestrzeni nazw.|  
    |Util-2|Definiowanie zmiennej, `returnValue`i zainicjować jej do `null` (C#) lub `Nothing` (Visual Basic).|  
    |Util-3|Nawet po wprowadzeniu `connString` jako nazwę parametrów połączenia w **właściwości** okna, należy określić `"SimpleDataApp.Properties.Settings.connString"` (C#) lub `"SimpleDataApp.My.MySettings.connString"` (Visual Basic) w kodzie.|  
  
##  <a name="BKMK_writethecodefortheforms"></a> Pisanie kodu dla formularzy  
 Ta sekcja zawiera krótkie przeglądy tego co wykonuje każdy formularz oraz pokazuje kod tworzący formularze. Ponumerowane komentarze identyfikują sekcje kodu.  
  
### <a name="navigation-form"></a>Formularz nawigacji  
 Formularz nawigacji otwiera się po uruchomieniu aplikacji. **Dodaj konto** przycisk służy do otwierania formularza NewCustomer. **Realizuj lub Anuluj zamówienia** przycisk służy do otwierania formularza FillOrCancel. **Zakończenia** przycisk zamyka aplikację.  
  
#### <a name="make-the-navigation-form-the-startup-form"></a>Wykonaj formularz początkowy formularz nawigacji  
 Jeśli używasz języka C# w **Eksploratora rozwiązań**, otwórz plik Program.cs, a następnie zmień `Application.Run` wiersz do tego: `Application.Run(new Navigation());`  
  
 Jeśli używasz języka Visual Basic w **Eksploratora rozwiązań**, otwórz **właściwości** wybierz **aplikacji** , a następnie wybierz pozycję  **SimpleDataApp.Navigation** w **formularz początkowy** listy.  
  
#### <a name="create-event-handlers"></a>Tworzenie obsługi zdarzeń  
 Kliknij dwukrotnie trzech przycisków w formularzu, aby utworzyć metody pusty program obsługi zdarzeń.  
  
#### <a name="create-code-for-navigation"></a>Utwórz kod dla nawigacji  
 W formularzu Nawigacja Zastąp istniejący kod następującym kodem.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
  
namespace SimpleDataApp  
{  
    public partial class Navigation : Form  
    {  
        public Navigation()  
        {  
            InitializeComponent();  
        }  
  
        //Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.  
        private void btnGoToAdd_Click(object sender, EventArgs e)  
        {  
            Form frm = new NewCustomer();  
            frm.Show();  
        }  
  
        //Open the FillorCancel form as a dialog box.  
        private void btnGoToFillOrCancel_Click(object sender, EventArgs e)  
        {  
            Form frm = new FillOrCancel();  
            frm.ShowDialog();  
        }  
  
        //Close the application, not just the Navigation form.  
        private void btnExit_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
  
Namespace SimpleDataApp  
    Partial Public Class Navigation  
        Inherits Form  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.  
        Private Sub btnGoToAdd_Click() Handles btnGoToAdd.Click  
            Dim frm As Form = New NewCustomer()  
            frm.Show()  
        End Sub  
  
        ' Open the FillorCancel form as a dialog box.  
        Private Sub btnGoToFillOrCancel_Click() Handles btnGoToFillOrCancel.Click  
            Dim frm As Form = New FillOrCancel()  
            frm.ShowDialog()  
        End Sub  
  
        ' Close the application, not just the Navigation form.  
        Private Sub btnExit_Click() Handles btnExit.Click  
            Me.Close()  
        End Sub  
    End Class  
End Namespace  
  
```  
  
### <a name="newcustomer-form"></a>Formularz NewCustomer  
 Kiedy wpisujesz nazwę klienta, a następnie wybierz pozycję **Utwórz konto** przycisk, formularz NewCustomer tworzy konto klienta, a program SQL Server zwraca wartość IDENTITY jako nowy numer konta. Następnie można złożyć zamówienia na nowe konto, określając wielkość i datę zamówienia i wybierając **złóż zamówienie** przycisku.  
  
#### <a name="create-event-handlers"></a>Tworzenie obsługi zdarzeń  
 Utwórz puste kliknij obsługi zdarzeń dla każdego przycisku w formularzu.  
  
#### <a name="create-code-for-newcustomer"></a>Utwórz kod dla NewCustomer  
 Dodaj następujący kod do formularza NewCustomer. Krok przez każdy blok kodu przy użyciu ponumerowanych komentarzy i tabelę po kodzie.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
//NC-1 More namespaces.  
using System.Data.SqlClient;  
using System.Configuration;  
  
namespace SimpleDataApp  
{  
    public partial class NewCustomer : Form  
    {  
        //NC-2 Storage for IDENTITY values returned from database.  
        private int parsedCustomerID;  
        private int orderID;  
  
        //NC-3 Specify a connection string.  
        string connstr = SimpleDataApp.Utility.GetConnectionString();  
  
        public NewCustomer()  
        {  
            InitializeComponent();  
        }  
  
        //NC-4 Create account.  
        private void btnCreateAccount_Click(object sender, EventArgs e)  
        {  
            //NC-5 Set up and run stored procedure only if Customer Name is present.  
            if (isCustomerName())  
            {  
  
                //NC-6 Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //NC-7 Create a SqlCommand, and identify it as a stored procedure.  
                SqlCommand cmdNewCustomer = new SqlCommand("Sales.uspNewCustomer", conn);  
                cmdNewCustomer.CommandType = CommandType.StoredProcedure;  
  
                //NC-8 Add input parameter from the stored procedure and specify what to use as its value.  
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerName", SqlDbType.NVarChar, 40));  
                cmdNewCustomer.Parameters["@CustomerName"].Value = txtCustomerName.Text;  
  
                //NC-9 Add output parameter.  
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));  
                cmdNewCustomer.Parameters["@CustomerID"].Direction = ParameterDirection.Output;  
  
                //NC-10 try-catch-finally  
                try  
                {  
                    //NC-11 Open the connection.  
                    conn.Open();  
  
                    //NC-12 Run the stored procedure.  
                    cmdNewCustomer.ExecuteNonQuery();  
  
                    //NC-13 Customer ID is an IDENTITY value from the database.   
                    this.parsedCustomerID = (int)cmdNewCustomer.Parameters["@CustomerID"].Value;  
                    this.txtCustomerID.Text = Convert.ToString(parsedCustomerID);  
  
                }  
                catch  
                {  
                    //NC-14 A simple catch.  
  
                    MessageBox.Show("Customer ID was not returned. Account could not be created.");  
                }  
                finally  
                {  
                    //NC-15 Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //NC-16 Verify that Customer Name is present.  
        private bool isCustomerName()  
        {  
            if (txtCustomerName.Text == "")  
            {  
                MessageBox.Show("Please enter a name.");  
                return false;  
            }  
            else  
            {  
                return true;  
            }  
        }  
  
        //NC-17 Place order.  
        private void btnPlaceOrder_Click(object sender, EventArgs e)  
        {  
            //NC-18 Set up and run stored procedure only if required input is present.  
            if (isPlaceOrderReady())  
            {  
                // Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //NC-19 Create SqlCommand and identify it as a stored procedure.  
                SqlCommand cmdNewOrder = new SqlCommand("Sales.uspPlaceNewOrder", conn);  
                cmdNewOrder.CommandType = CommandType.StoredProcedure;  
  
                //NC-20 @CustomerID, which was an output parameter from uspNewCustomer.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));  
                cmdNewOrder.Parameters["@CustomerID"].Value = this.parsedCustomerID;  
  
                //NC-21 @OrderDate.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@OrderDate", SqlDbType.DateTime, 8));  
                cmdNewOrder.Parameters["@OrderDate"].Value = dtpOrderDate.Value;  
  
                //NC-22 @Amount.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Amount", SqlDbType.Int));  
                cmdNewOrder.Parameters["@Amount"].Value = numOrderAmount.Value;  
  
                //NC-23 @Status. For a new order, the status is always O (open).  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Status", SqlDbType.Char, 1));  
                cmdNewOrder.Parameters["@Status"].Value = "O";  
  
                //NC-24 Add return value for stored procedure, which is orderID.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@RC", SqlDbType.Int));  
                cmdNewOrder.Parameters["@RC"].Direction = ParameterDirection.ReturnValue;  
  
                //try-catch-finally  
                try  
                {  
                    //Open connection.  
                    conn.Open();  
  
                    //Run the stored procedure.  
                    cmdNewOrder.ExecuteNonQuery();  
  
                    //NC-25 Display the order number.  
                    this.orderID = (int)cmdNewOrder.Parameters["@RC"].Value;  
                    MessageBox.Show("Order number " + this.orderID + " has been submitted.");  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("Order could not be placed.");  
                }  
                finally  
                {  
                    //Close connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //NC-26 Verify that order data is ready.  
        private bool isPlaceOrderReady()  
        {  
            // Verify that CustomerID is present.  
            if (txtCustomerID.Text == "")  
            {  
                MessageBox.Show("Please create customer account before placing order.");  
                return false;  
            }  
  
            // Verify that Amount isn't 0.   
            else if ((numOrderAmount.Value < 1))  
            {  
                MessageBox.Show("Please specify an order amount.");  
                return false;  
            }  
            else  
            {  
                // Order can be submitted.  
                return true;  
            }  
        }  
  
        //NC-27 Reset the form for another new account.  
        private void btnAddAnotherAccount_Click(object sender, EventArgs e)  
        {  
            this.ClearForm();  
        }  
  
        //NC-28 Clear values from controls.  
        private void ClearForm()  
        {  
            txtCustomerName.Clear();  
            txtCustomerID.Clear();  
            dtpOrderDate.Value = DateTime.Now;  
            numOrderAmount.Value = 0;  
            this.parsedCustomerID = 0;  
        }  
  
        //NC-29 Close the form.  
        private void btnAddFinish_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
  
    }  
}  
  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
' NC-1 More namespaces.  
Imports System.Data.SqlClient  
Imports System.Configuration  
  
Namespace SimpleDataApp  
    Partial Public Class NewCustomer  
        Inherits Form  
  
        ' NC-2 Storage for IDENTITY values returned from database.  
        Private parsedCustomerID As Integer  
        Private orderID As Integer  
  
        ' NC-3 Specify a connection string.  
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' NC-4 Create account.  
        Private Sub btnCreateAccount_Click() Handles btnCreateAccount.Click  
  
            ' NC-5 Set up and run stored procedure only if Customer Name is present.  
            If isCustomerName() Then  
  
                ' NC-6 Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' NC-7 Create a SqlCommand, and identify it as a stored procedure.  
                Dim cmdNewCustomer As New SqlCommand("Sales.uspNewCustomer", conn)  
                cmdNewCustomer.CommandType = CommandType.StoredProcedure  
  
                ' NC-8 Add input parameter from the stored procedure and specify what to use as its value.  
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerName", SqlDbType.NVarChar, 40))  
                cmdNewCustomer.Parameters("@CustomerName").Value = txtCustomerName.Text  
  
                ' NC-9 Add output parameter.  
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))  
                cmdNewCustomer.Parameters("@CustomerID").Direction = ParameterDirection.Output  
  
                ' NC-10 try-catch-finally  
                Try  
                    ' NC-11 Open the connection.  
                    conn.Open()  
  
                    ' NC-12 Run the stored procedure.  
                    cmdNewCustomer.ExecuteNonQuery()  
  
                    ' NC-13 Customer ID is an IDENTITY value from the database.   
                    Me.parsedCustomerID = CInt(cmdNewCustomer.Parameters("@CustomerID").Value)  
                    Me.txtCustomerID.Text = Convert.ToString(parsedCustomerID)  
  
                Catch  
                    ' NC-14 A simple catch.  
                    MessageBox.Show("Customer ID was not returned. Account could not be created.")  
                Finally  
                    ' NC-15 Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' NC-16 Verify that Customer Name is present.  
        Private Function isCustomerName() As Boolean  
            If txtCustomerName.Text = "" Then  
                MessageBox.Show("Please enter a name.")  
                Return False  
            Else  
                Return True  
            End If  
        End Function  
  
        ' NC-17 Place order.  
        Private Sub btnPlaceOrder_Click() Handles btnPlaceOrder.Click  
  
            ' NC-18 Set up and run stored procedure only if necessary input is present.  
            If isPlaceOrderReady() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' NC-19 Create SqlCommand and identify it as a stored procedure.  
                Dim cmdNewOrder As New SqlCommand("Sales.uspPlaceNewOrder", conn)  
                cmdNewOrder.CommandType = CommandType.StoredProcedure  
  
                ' NC-20 @CustomerID, which was an output parameter from uspNewCustomer.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))  
                cmdNewOrder.Parameters("@CustomerID").Value = Me.parsedCustomerID  
  
                ' NC-21 @OrderDate.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@OrderDate", SqlDbType.DateTime, 8))  
                cmdNewOrder.Parameters("@OrderDate").Value = dtpOrderDate.Value  
  
                ' NC-22 @Amount.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@Amount", SqlDbType.Int))  
                cmdNewOrder.Parameters("@Amount").Value = numOrderAmount.Value  
  
                ' NC-23 @Status. For a new order, the status is always O (open).  
                cmdNewOrder.Parameters.Add(New SqlParameter("@Status", SqlDbType.[Char], 1))  
                cmdNewOrder.Parameters("@Status").Value = "O"  
  
                ' NC-24 Add return value for stored procedure, which is orderID.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@RC", SqlDbType.Int))  
                cmdNewOrder.Parameters("@RC").Direction = ParameterDirection.ReturnValue  
  
                ' try-catch-finally  
                Try  
                    ' Open connection.  
                    conn.Open()  
  
                    ' Run the stored procedure.  
                    cmdNewOrder.ExecuteNonQuery()  
  
                    ' NC-25 Display the order number.  
                    Me.orderID = CInt(cmdNewOrder.Parameters("@RC").Value)  
                    MessageBox.Show("Order number " & (Me.orderID).ToString & " has been submitted.")  
  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("Order could  not be placed.")  
  
                Finally  
                    ' Close connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' NC-26 Verify that order data is ready.  
        Private Function isPlaceOrderReady() As Boolean  
  
            ' Verify that CustomerID is present.  
            If txtCustomerID.Text = "" Then  
                MessageBox.Show("Please create customer account before placing order.")  
                Return False  
  
                ' Verify that Amount isn't 0.   
            ElseIf (numOrderAmount.Value < 1) Then  
  
                MessageBox.Show("Please specify an order amount.")  
                Return False  
            Else  
                ' Order can be submitted.  
                Return True  
            End If  
        End Function  
  
        ' NC-27 Reset the form for another new account.  
        Private Sub btnAddAnotherAccount_Click() Handles btnAddAnotherAccount.Click  
            Me.ClearForm()  
        End Sub  
  
        ' NC-28 Clear values from controls.  
        Private Sub ClearForm()  
            txtCustomerName.Clear()  
            txtCustomerID.Clear()  
            dtpOrderDate.Value = DateTime.Now  
            numOrderAmount.Value = 0  
            Me.parsedCustomerID = 0  
        End Sub  
  
        ' NC-29 Close the form.  
        Private Sub btnAddFinish_Click() Handles btnAddFinish.Click  
            Me.Close()  
        End Sub  
  
    End Class  
End Namespace  
```  
  
|Komentarz|Opis|  
|-------------|-----------------|  
|NC-1|Dodaj `System.Data.SqlClient` i `System.Configuration` do listy obszarów nazw.|  
|NC-2|Zadeklaruj `parsedCustomerID` i `orderID` zmiennych, które będą używane później.|  
|NC-3|Wywołaj `GetConnectionString` metodę, aby pobrać parametry połączenia z pliku konfiguracyjnego aplikacji, a wartość jest przechowywana w `connstr` zmiennej ciągu.|  
|NC-4|Dodaj kod do obsługi zdarzeń kliknij `btnCreateAccount` przycisku.|  
|NC-5|Opakować wywołanie `isCustomerName` wokół kodu zdarzenia, aby `uspNewCustomer` działa tylko wtedy, gdy obecna jest nazwa klienta.|  
|NC-6|Tworzenie `SqlConnection` obiektu (`conn`) i przekaż w ciągu połączenia w `connstr`.|  
|NC-7|Tworzenie `SqlCommand` obiektu `cmdNewCustomer`.<br /><br /> -Określ `Sales.uspNewCustomer` jako procedurę przechowywaną do uruchomienia.<br />-Użyj `CommandType` właściwości w celu określenia, że polecenie jest przechowywaną procedurą.|  
|NC-8|Dodaj `@CustomerName` parametr wejściowy z procedury składowanej.<br /><br /> — Dodać parametr do `Parameters` kolekcji.<br />-Użyj `SqlDbType` wyliczeniu, aby określić typ parametru jako nvarchar(40).<br />-Określ `txtCustomerName.Text` jako źródło.|  
|NC-9|Dodaj parametr wejściowy z procedury składowanej.<br /><br /> — Dodać parametr do `Parameters` kolekcji.<br />-Użyj `ParameterDirection.Output` Aby zidentyfikować parametr jako dane wyjściowe.|  
|NC-10|Dodaj Blok Try-Catch-Finally, aby otworzyć połączenie, uruchom procedurę składowaną, obsługa wyjątków, a następnie zamknij połączenie.|  
|NC-11|Otwórz połączenie (`conn`) utworzone w NC-6.|  
|NC-12|Użyj `ExecuteNonQuery` metodę `cmdNewCustomer` do uruchomienia `Sales.uspNewCustomer` procedury składowanej. To przechowywane procedury przebiegów `INSERT` instrukcji, nie zapytanie.|  
|NC-13|`@CustomerID` Wartość jest zwracana jako wartość tożsamości z bazy danych. Ponieważ jest to liczba całkowita, musisz przekonwertować go na ciąg, aby wyświetlić ją w **identyfikator klienta** pola tekstowego.<br /><br /> — Można zadeklarować `parsedCustomerID` w NC-2.<br />-Store `@CustomerID` wartość w `parsedCustomerID` do późniejszego użycia.<br />-Konwertuj zwracany Identyfikatro klienta na ciąg i włóż go do `txtCustomerID.Text`.|  
|NC-14|W tym przykładzie Dodaj prostą klauzuli catch (niemającą jakości produkcyjnej).|  
|NC-15|Zawsze zamykaj połączenie po zakończeniu korzystania z niego, tak aby mogło być ono zwolnione z puli połączeń. Zobacz [połączenie serwera SQL Server (ADO.NET) buforowanie](http://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx).|  
|NC-16|Zdefiniuj metodę, aby sprawdzić, czy nazwa klienta jest obecna.<br /><br /> — Jeśli pole tekstowe jest puste, wyświetlany komunikat i zwracają `false`, ponieważ nazwa jest wymagana do utworzenia konta.<br />— Jeśli pole tekstowe nie jest pusta, zwróć `true`.|  
|NC-17|Dodaj kod do obsługi zdarzeń kliknij `btnPlaceOrder` przycisku.|  
|NC-18|Opakować wywołanie `isPlaceOrderReady` wokół `btnPlaceOrder_Click` kodu zdarzenia, aby `uspPlaceNewOrder` nie działa, jeśli jest to wymagane dane wejściowe nie będą dostępne.|  
|NC-19 poprzez NC-25|Te sekcje kodu odpowiadają kodowi dodanemu przez dodano dla `btnCreateAccount_Click` programu obsługi zdarzeń.<br /><br /> -   NC-19. Tworzenie `SqlCommand` obiektu `cmdNewOrder`, a następnie określ `Sales.uspPlaceOrder` jako procedurę przechowywaną.<br />-NC-20 do NC 23 są parametrami wejściowymi dla procedury składowanej.<br />-   NC-24. `@RC` będzie zawierać zwracanej wartości, która jest identyfikator zamówieniem wygenerowany z bazy danych. Kierunek tego parametru jest określony jako `ReturnValue`.<br />-   NC-25. Wartość Identyfikatora zamówienia w Store `orderID` zmiennej zadeklarowanej w NC-2 i Wyświetl tę wartość, w oknie komunikatu.|  
|NC-26|Zdefiniuj metodę, aby sprawdzić, czy istnieje identyfikator klienta i że kwota została określona w `numOrderAmount`.|  
|NC-27|Wywołaj `ClearForm` method in Class metoda `btnAddAnotherAccount` program obsługi zdarzeń kliknięcia.|  
|NC-28|Utwórz `ClearForm` metodę, aby wyczyścić wartości z formularza, jeśli chcesz dodać innego klienta.|  
|NC29|Zamknij formularz NewCustomer i ponowne Ustawianie fokusa na formularzu nawigacji.|  
  
### <a name="fillorcancel-form"></a>Formularz FillOrCancel  
 Formularz FillorCancel uruchamia zapytanie do zwrotu zamówienia, gdy wprowadzasz identyfikator zamówienia i wybierz **Znajdź zamówienie** przycisku. Zwracany wiersz wyświetla się w siatce danych tylko do odczytu. Możesz oznaczyć porządek jako anulowany (X), jeśli zostanie wybrana **Anuluj porządek** przycisku, lub możesz oznaczyć porządek jako wypełniony (F) po wybraniu **Wypełnij porządek** przycisku. Jeśli wybierzesz **Znajdź zamówienie** przycisk ponownie, pojawi się uaktualniony wiersz.  
  
#### <a name="create-event-handlers"></a>Tworzenie obsługi zdarzeń  
 Utwórz puste kliknij obsługi zdarzeń dla czterech przycisków w formularzu.  
  
#### <a name="create-code-for-fillorcancel"></a>Utwórz kod dla FillOrCancel  
 Dodaj następujący kod do formularza FillOrCancel. Kroku przez bloki kodu przy użyciu ponumerowanych komentarzy i tabelę, która znajduje się po kodzie.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
//FC-1 More namespaces.  
using System.Text.RegularExpressions;  
using System.Data.SqlClient;  
using System.Configuration;  
  
namespace SimpleDataApp  
{  
    public partial class FillOrCancel : Form  
    {  
        //FC-2 Storage for OrderID.  
        private int parsedOrderID;  
  
        //FC-3 Specify a connection string.  
        string connstr = SimpleDataApp.Utility.GetConnectionString();  
  
        public FillOrCancel()  
        {  
            InitializeComponent();  
        }  
  
        //FC-4 Find an order.  
        private void btnFindByOrderID_Click(object sender, EventArgs e)  
        {  
            //FC-5 Prepare the connection and the command.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //Define a query string that has a parameter for orderID.  
                string sql = "select * from Sales.Orders where orderID = @orderID";  
  
                //Create a SqlCommand object.  
                SqlCommand cmdOrderID = new SqlCommand(sql, conn);  
  
                //Define the @orderID parameter and its value.  
                cmdOrderID.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdOrderID.Parameters["@orderID"].Value = parsedOrderID;  
  
                //try-catch-finally  
                try  
                {  
                    //FC-6 Run the command and display the results.  
                    //Open the connection.  
                    conn.Open();  
  
                    //Run the command by using SqlDataReader.  
                    SqlDataReader rdr = cmdOrderID.ExecuteReader();  
  
                    //Create a data table to hold the retrieved data.  
                    DataTable dataTable = new DataTable();  
  
                    //Load the data from SqlDataReader into the data table.  
                    dataTable.Load(rdr);  
  
                    //Display the data from the data table in the data grid view.  
                    this.dgvCustomerOrders.DataSource = dataTable;  
  
                    //Close the SqlDataReader.  
                    rdr.Close();  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("The requested order could not be loaded into the form.");  
                }  
                finally  
                {  
                    //Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-7 Cancel an order.  
        private void btnCancelOrder_Click(object sender, EventArgs e)  
        {  
            //Set up and run stored procedure only if OrderID is ready.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                // Create command and identify it as a stored procedure.  
                SqlCommand cmdCancelOrder = new SqlCommand("Sales.uspCancelOrder", conn);  
                cmdCancelOrder.CommandType = CommandType.StoredProcedure;  
  
                cmdCancelOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdCancelOrder.Parameters["@orderID"].Value = parsedOrderID;  
  
                // try-catch-finally  
                try  
                {  
                    // Open the connection.  
                    conn.Open();  
  
                    // Run the cmdCancelOrder command.  
                    cmdCancelOrder.ExecuteNonQuery();  
                }  
                // A simple catch.  
                catch  
                {  
                    MessageBox.Show("The cancel operation was not completed.");  
                }  
                finally  
                {  
                    //Close connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-8 Fill an order.  
        private void btnFillOrder_Click(object sender, EventArgs e)  
        {  
            //Set up and run stored procedure only if OrderID is ready.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //Create command and identify it as a stored procedure.  
                SqlCommand cmdFillOrder = new SqlCommand("Sales.uspFillOrder", conn);  
                cmdFillOrder.CommandType = CommandType.StoredProcedure;  
  
                // Add input parameter from the stored procedure.  
                cmdFillOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdFillOrder.Parameters["@orderID"].Value = parsedOrderID;  
  
                //Add the second input parameter.  
                cmdFillOrder.Parameters.Add(new SqlParameter("@FilledDate", SqlDbType.DateTime, 8));  
                cmdFillOrder.Parameters["@FilledDate"].Value = dtpFillDate.Value;  
  
                //try-catch-finally  
                try  
                {  
                    //Open the connection.  
                    conn.Open();  
  
                    //Run the cmdFillOrder command.  
                    cmdFillOrder.ExecuteNonQuery();  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("The fill operation was not completed.");  
                }  
                finally  
                {  
                    //Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-9 Verify that OrderID is ready.  
        private bool isOrderID()  
        {  
  
            //Check for input in the Order ID text box.  
            if (txtOrderID.Text == "")  
            {  
                MessageBox.Show("Please specify the Order ID.");  
                return false;  
            }  
  
            // Check for characters other than integers.  
            else if (Regex.IsMatch(txtOrderID.Text, @"^\D*$"))  
            {  
               //Show message and clear input.  
                MessageBox.Show("Please specify integers only.");  
                txtOrderID.Clear();  
                return false;  
            }  
            else  
            {  
                //Convert the text in the text box to an integer to send to the database.  
                parsedOrderID = Int32.Parse(txtOrderID.Text);  
                return true;  
            }  
        }  
  
        //Close the form.  
        private void btnFinishUpdates_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
' FC-1 More namespaces.  
Imports System.Text.RegularExpressions  
Imports System.Data.SqlClient  
Imports System.Configuration  
  
Namespace SimpleDataApp  
    Partial Public Class FillOrCancel  
        Inherits Form  
        ' FC-2 Storage for OrderID.  
        Private parsedOrderID As Integer  
  
        ' FC-3 Specify a connection string.  
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' FC-4 Find an order.  
        Private Sub btnFindByOrderID_Click() Handles btnFindByOrderID.Click  
  
            ' FC-5 Prepare the connection and the command.  
  
            If isOrderID() Then  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Define the query string that has a parameter for orderID.  
                Dim sql As String = "select * from Sales.Orders where orderID = @orderID"  
  
                ' Create a SqlCommand object.  
                Dim cmdOrderID As New SqlCommand(sql, conn)  
  
                ' Define the @orderID parameter and its value.  
                cmdOrderID.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdOrderID.Parameters("@orderID").Value = parsedOrderID  
  
                ' try-catch-finally  
                Try  
                    ' FC-6 Run the command and display the results.  
                    ' Open connection.  
                    conn.Open()  
  
                    ' Run the command by using SqlDataReader.  
                    Dim rdr As SqlDataReader = cmdOrderID.ExecuteReader()  
  
                    ' Create a data table to hold the retrieved data.  
                    Dim dataTable As New DataTable()  
  
                    ' Load the data from SqlDataReader into the data table.  
                    dataTable.Load(rdr)  
  
                    ' Display the data from the data table in the data grid view.  
                    Me.dgvCustomerOrders.DataSource = dataTable  
  
                    ' Close the SqlDataReader.  
                    rdr.Close()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The requested order could not be loaded into the form.")  
                Finally  
                    ' Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-7 Cancel an order.  
        Private Sub btnCancelOrder_Click() Handles btnCancelOrder.Click  
  
            ' Set up and run stored procedure only if OrderID is ready.  
            If isOrderID() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Create the command and identify it as a stored procedure.  
                Dim cmdCancelOrder As New SqlCommand("Sales.uspCancelOrder", conn)  
                cmdCancelOrder.CommandType = CommandType.StoredProcedure  
  
                ' Add input parameter from the stored procedure.  
                cmdCancelOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdCancelOrder.Parameters("@orderID").Value = parsedOrderID  
  
                ' try-catch-finally  
                Try  
                    ' Open the connection.  
                    conn.Open()  
  
                    ' Run the cmdCancelOrder command.  
                    cmdCancelOrder.ExecuteNonQuery()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The cancel operation was not completed.")  
                Finally  
                    ' Close connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-8 Fill an order.  
        Private Sub btnFillOrder_Click() Handles btnFillOrder.Click  
  
            ' Set up and run stored procedure only if OrderID is ready.  
            If isOrderID() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Create command and identify it as a stored procedure.  
                Dim cmdFillOrder As New SqlCommand("Sales.uspFillOrder", conn)  
                cmdFillOrder.CommandType = CommandType.StoredProcedure  
  
                ' Add input parameter from the stored procedure.  
                cmdFillOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdFillOrder.Parameters("@orderID").Value = parsedOrderID  
  
                ' Add second input parameter.  
                cmdFillOrder.Parameters.Add(New SqlParameter("@FilledDate", SqlDbType.DateTime, 8))  
                cmdFillOrder.Parameters("@FilledDate").Value = dtpFillDate.Value  
  
                ' try-catch-finally  
                Try  
                    ' Open the connection.  
                    conn.Open()  
  
                    ' Run the cmdFillOrder command.   
                    cmdFillOrder.ExecuteNonQuery()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The fill operation was not completed.")  
                Finally  
                    ' Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-9 Verify that OrderID is ready.  
        Private Function isOrderID() As Boolean  
  
            ' Check for input in the Order ID text box.  
            If txtOrderID.Text = "" Then  
                MessageBox.Show("Please specify the Order ID.")  
                Return False  
  
                ' Check for characters other than integers.  
            ElseIf Regex.IsMatch(txtOrderID.Text, "^\D*$") Then  
  
                ' Show message and clear input.  
                MessageBox.Show("Please specify integers only.")  
                txtOrderID.Clear()  
                Return False  
  
            Else  
                ' Convert the text in the text box to an integer to send to the database.  
                parsedOrderID = Int32.Parse(txtOrderID.Text)  
                Return True  
  
            End If  
        End Function  
  
        ' Close the form.  
        Private Sub btnFinishUpdates_Click() Handles btnFinishUpdates.Click  
            Me.Close()  
        End Sub  
    End Class  
End Namespace  
```  
  
|Komentarz|Opis|  
|-------------|-----------------|  
|FC-1|Dodaj `System.Data.SqlClient`, `System.Configuration`, i `System.Text.RegularExpressions` do listy obszarów nazw.|  
|FC-2|Zadeklaruj `parsedOrderID` zmiennej.|  
|FC-3|Wywołaj `GetConnectionString` metodę, aby pobrać parametry połączenia z pliku konfiguracyjnego aplikacji, a wartość jest przechowywana w `connstr` zmiennej ciągu.|  
|FC-4|Dodaj kod do obsługi zdarzeń kliknij `btnFindOrderByID`.|  
|FC-5|Te zadania są wymagane, zanim zostanie podjęta próba uruchomienia instrukcji SQL lub procedury składowanej.<br /><br /> -Tworzenie `SqlConnection` obiektu.<br />— Zdefiniuj instrukcję SQL lub określ nazwę procedury składowanej. (W tym przypadku uruchomisz `SELECT` instrukcja.)<br />-Tworzenie `SqlCommand` obiektu.<br />-Definiowanie parametrów dla instrukcji SQL lub procedury składowanej.|  
|FC-6|Ten kod używa `SqlDataReader` i `DataTable` należy pobrać i wyświetlić wynik zapytania.<br /><br /> — Otwórz połączenie.<br />-Tworzenie `SqlDataReader` obiektu `rdr`, uruchamiając `ExecuteReader` metodę `cmdOrderID`.<br />-Tworzenie `DataTable` obiekt do przechowywania pobranych danych.<br />-Ładowanie danych z `SqlDataReader` do obiektu `DataTable` obiektu.<br />— Wyświetlanie danych w widoku siatki danych, określając `DataTable` jako `DataSource` dla widoku siatki danych.<br />— Zamknij `SqlDataReader`.|  
|FC-7|Dodaj kod do obsługi zdarzeń kliknij `btnCancelOrder`. Ten kod uruchamia `Sales.uspCancelOrder` procedury składowanej.|  
|FC-8|Dodaj kod do obsługi zdarzeń kliknij `btnFillOrder`. Ten kod uruchamia `Sales.uspFillOrder` procedury składowanej.|  
|FC-9|Utwórz metodę, aby sprawdzić, czy `OrderID` jest gotowy do przesłania jako parametr do `SqlCommand` obiektu.<br /><br /> -Upewnij się, że identyfikator został wprowadzony w `txtOrderID`.<br />-Użyj `Regex.IsMatch` Aby zdefiniować prostą kontrolę wykrywającą znaki nie będące.<br />— Można zadeklarować `parsedOrderID` zmiennej w FC-2.<br />— Jeśli dane wejściowe są prawidłowe, Konwertuj tekst na liczbę całkowitą, a wartość jest przechowywana w `parsedOrderID` zmiennej.<br />-Opakować `isOrderID` metoda wokół `btnFindByOrderID`, `btnCancelOrder`, i `btnFillOrder` kliknij obsługi zdarzeń.|  
  
##  <a name="BKMK_testyourapplication"></a> Testowanie aplikacji  
 Wybierz klawisz F5, aby skompilować i przetestować aplikację po zakodowaniu każdej obsługi zdarzenia Click, a następnie po zakończenia kodowania.
