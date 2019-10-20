---
title: Tworzenie prostej aplikacji danych przy użyciu usługi ADO.NET | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b524c9d630f30edd226265ac150ef7ec4f6c60d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651074"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Tworzenie prostej aplikacji do obsługi danych za pomocą pakietu ADO.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas tworzenia aplikacji, która operuje na danych w bazie danych, wykonywane są podstawowe zadania, takie jak Definiowanie parametrów połączenia, wstawianie danych i uruchamianie procedur składowanych. Postępując zgodnie z tym tematem, można dowiedzieć się, jak korzystać z bazy danych z poziomu prostej Windows Forms "Formularze danych" przy użyciu C# wizualizacji lub Visual Basic i ADO.NET.  Wszystkie technologie danych platformy .NET, w tym zestawy, LINQ to SQL i Entity Framework, ostatecznie wykonują czynności, które są bardzo podobne do tych, które przedstawiono w tym artykule.

 W tym artykule przedstawiono prosty sposób pobierania danych z bazy danych w bardzo szybki sposób. Jeśli aplikacja wymaga modyfikacji danych w sposób nieuproszczony i zaktualizowania bazy danych, należy rozważyć użycie Entity Framework i użycie powiązania danych w celu automatycznego synchronizowania kontrolek interfejsu użytkownika z zmianami danych źródłowych.

> [!IMPORTANT]
> Aby zachować prosty kod, nie obejmuje obsługi wyjątków gotowych do produkcji.

 **W tym temacie**

- [Konfigurowanie przykładowej bazy danych](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)

- [Tworzenie formularzy i Dodawanie kontrolek](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)

- [Przechowywanie parametrów połączenia](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)

- [Pobierz parametry połączenia](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)

- [Napisz kod dla formularzy](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)

- [Testowanie aplikacji](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)

## <a name="prerequisites"></a>Wymagania wstępne
 Aby można było utworzyć aplikację, potrzebne są:

- Visual Studio Community Edition.

- SQL Server Express LocalDB.

- Niewielka Przykładowa baza danych, którą tworzysz, wykonując kroki opisane w temacie [Tworzenie bazy danych SQL przy użyciu skryptu](../data-tools/create-a-sql-database-by-using-a-script.md).

- Parametry połączenia dla bazy danych po jej skonfigurowaniu. Tę wartość można znaleźć, otwierając **Eksplorator obiektów SQL Server**, otwierając menu skrótów dla bazy danych, wybierając **Właściwości**, a następnie przewijając do właściwości **ConnectionString** .

  W tym temacie założono, że znasz podstawowe funkcje środowiska IDE programu Visual Studio i można utworzyć Windows Forms aplikację, dodać formularze do tego projektu, umieścić przyciski i inne kontrolki na tych formularzach, ustawić właściwości tych formantów i prostych zdarzeń kodu . Jeśli nie masz doświadczenia z tymi zadaniami, zalecamy ukończenie [wprowadzenie przy użyciu C# wizualizacji i Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) przed uruchomieniem tego tematu.

## <a name="BKMK_setupthesampledatabase"></a>Konfigurowanie przykładowej bazy danych
 Przykładowa baza danych dla tego instruktażu składa się z tabel klienta i zamówień. Tabele nie zawierają początkowo żadnych danych, ale po uruchomieniu aplikacji, którą utworzysz, należy dodać dane. Baza danych ma również pięć prostych procedur składowanych. [Tworzenie bazy danych SQL przy użyciu skryptu](../data-tools/create-a-sql-database-by-using-a-script.md) zawiera skrypt Transact-SQL, który tworzy tabele, klucze podstawowe i obce, ograniczenia oraz procedury składowane.

## <a name="BKMK_createtheformsandaddcontrols"></a>Tworzenie formularzy i Dodawanie kontrolek

1. Utwórz projekt dla Windows Forms aplikacji, a następnie nadaj mu nazwę SimpleDataApp.

    Program Visual Studio tworzy projekt i kilka plików, w tym pusty formularz systemu Windows o nazwie Form1.

2. Dodaj dwa formularze systemu Windows do projektu, tak aby miało trzy formy, a następnie nadaj im następujące nazwy:

   - Nawigacja

   - NewCustomer

   - FillOrCancel

3. Dla każdego formularza Dodaj pola tekstowe, przyciski i inne kontrolki, które pojawiają się na poniższych ilustracjach. Dla każdej kontrolki ustaw właściwości, które opisano w tabelach.

   > [!NOTE]
   > Pola Grupa i kontrolki etykieta umożliwiają dodawanie przejrzystości, ale nie są używane w kodzie.

   **Formularz nawigacji**

   ![Okno dialogowe nawigacji](../data-tools/media/simpleappnav.png "SimpleAppNav")

|Kontrolki formularza nawigacji|Właściwości|
|--------------------------------------|----------------|
|Przycisk|Nazwa = btnGoToAdd|
|Przycisk|Nazwa = btnGoToFillOrCancel|
|Przycisk|Nazwa = btnExit|

 **Formularz NewCustomer**

 ![Dodaj nowego klienta i umieść zamówienie](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")

|Kontrolki formularza NewCustomer|Właściwości|
|---------------------------------------|----------------|
|TextBox|Nazwa = txtCustomerName|
|TextBox|Nazwa = txtCustomerID<br /><br /> ReadOnly = true|
|Przycisk|Nazwa = btnCreateAccount|
|NumericUpdown|DecimalPlaces = 0<br /><br /> Maksimum = 5000<br /><br /> Nazwa = numOrderAmount|
|DateTimePicker|Format = Short<br /><br /> Nazwa = dtpOrderDate|
|Przycisk|Nazwa = btnPlaceOrder|
|Przycisk|Nazwa = btnAddAnotherAccount|
|Przycisk|Nazwa = btnAddFinish|

 **Formularz FillOrCancel**

 ![Wypełnij lub Anuluj zamówienia](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")

|Kontrolki formularza FillOrCancel|Właściwości|
|----------------------------------------|----------------|
|TextBox|Nazwa = txtOrderID|
|Przycisk|Nazwa = btnFindByOrderID|
|DateTimePicker|Format = Short<br /><br /> Nazwa = dtpFillDate|
|DataGridView|Nazwa = dgvCustomerOrders<br /><br /> ReadOnly = true<br /><br /> RowHeadersVisible = FAŁSZ|
|Przycisk|Nazwa = btnCancelOrder|
|Przycisk|Nazwa = btnFillOrder|
|Przycisk|Nazwa = btnFinishUpdates|

## <a name="BKMK_storetheconnectionstring"></a>Przechowywanie parametrów połączenia
 Gdy aplikacja próbuje otworzyć połączenie z bazą danych, aplikacja musi mieć dostęp do parametrów połączenia. Aby uniknąć wprowadzania ciągu ręcznie w każdym formularzu, należy przechowywać ciąg w pliku konfiguracji aplikacji w projekcie i utworzyć metodę zwracającą ciąg, gdy metoda jest wywoływana z dowolnej formy w aplikacji.

 Parametry połączenia można znaleźć w **Eksplorator obiektów SQL Server** przez kliknięcie prawym przyciskiem myszy bazy danych, wybranie **Właściwości**, a następnie znalezienie właściwości ConnectionString. Użyj kombinacji klawiszy Ctrl + A, aby wybrać ciąg.

1. W **Eksplorator rozwiązań**wybierz węzeł **Właściwości** w ramach projektu, a następnie wybierz pozycję **Ustawienia. ustawienia**.

2. W kolumnie **Nazwa** wprowadź `connString`.

3. Na liście **Typ** wybierz pozycję **(parametry połączenia)** .

4. Z listy **zakres** wybierz pozycję **aplikacja**.

5. W kolumnie **wartość** wprowadź parametry połączenia (bez żadnych cudzysłowów zewnętrznych), a następnie Zapisz zmiany.

> [!NOTE]
> W prawdziwej aplikacji należy przechowywać parametry połączenia bezpiecznie, zgodnie z opisem w temacie [Parametry połączenia i pliki konfiguracji](https://msdn.microsoft.com/library/37df2641-661e-407a-a3fb-7bf9540f01e8).

## <a name="BKMK_retrievetheconnectionstring"></a>Pobierz parametry połączenia

1. Na pasku menu wybierz kolejno opcje **projekt**  > **Dodaj odwołanie**, a następnie Dodaj odwołanie do elementu System. Configuration. dll.

2. Na pasku menu wybierz pozycję **projekt**  > **Dodaj klasę** , aby dodać plik klasy do projektu, a następnie Nazwij plik `Utility`.

     Program Visual Studio utworzy plik i wyświetli go w **Eksplorator rozwiązań**.

3. W pliku narzędzia Zastąp kod symbolu zastępczego poniższym kodem. Zwróć uwagę na ponumerowane Komentarze (poprzedzone znakiem util), które identyfikują sekcje kodu. Tabela, która następuje po kodzie wywołuje punkty klucza.

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
    |Util-1|Dodaj przestrzeń nazw `System.Configuration`.|
    |Util-2|Zdefiniuj zmienną, `returnValue` i zainicjuj ją do `null` (C#) lub `Nothing` (Visual Basic).|
    |Util-3|Mimo że wprowadzono `connString` jako nazwę parametrów połączenia w oknie **Właściwości** , należy określić `"SimpleDataApp.Properties.Settings.connString"` (C#) lub `"SimpleDataApp.My.MySettings.connString"` (Visual Basic) w kodzie.|

## <a name="BKMK_writethecodefortheforms"></a>Napisz kod dla formularzy
 Ta sekcja zawiera krótkie przeglądy działania poszczególnych formularzy i pokazuje kod, który tworzy formularze. Numerowane Komentarze identyfikują sekcje kodu.

### <a name="navigation-form"></a>Formularz nawigacji
 Po uruchomieniu aplikacji zostanie otwarty formularz nawigacji. Przycisk **Dodaj konto** otwiera formularz newCustomer. Przycisk **Wypełnij lub Anuluj zamówienia** powoduje otwarcie formularza FillOrCancel. Przycisk **Zakończ** zamyka aplikację.

#### <a name="make-the-navigation-form-the-startup-form"></a>Ustaw nawigację formularza startowego
 Jeśli używasz programu C#, w **Eksplorator rozwiązań**Otwórz program.cs, a następnie zmień wiersz `Application.Run` na: `Application.Run(new Navigation());`

 Jeśli używasz Visual Basic, w **Eksplorator rozwiązań**, Otwórz okno **Właściwości** , wybierz kartę **aplikacja** , a następnie wybierz pozycję **SimpleDataApp. Nawigacja** na liście **formularz startowy** .

#### <a name="create-event-handlers"></a>Tworzenie programów obsługi zdarzeń
 Kliknij dwukrotnie trzy przyciski w formularzu, aby utworzyć puste metody obsługi zdarzeń.

#### <a name="create-code-for-navigation"></a>Utwórz kod dla nawigacji
 W formularzu nawigacji Zastąp istniejący kod następującym kodem.

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
 Po wprowadzeniu nazwy klienta i wybraniu przycisku **Utwórz konto** formularz newCustomer tworzy konto klienta, a SQL Server zwraca wartość tożsamości jako nowy numer konta. Następnie możesz złożyć zamówienie dla nowego konta, określając kwotę i datę zamówienia, a następnie wybierając przycisk **Umieść zamówienie** .

#### <a name="create-event-handlers"></a>Tworzenie programów obsługi zdarzeń
 Utwórz pustą procedurę obsługi zdarzeń kliknięcia dla każdego przycisku w formularzu.

#### <a name="create-code-for-newcustomer"></a>Utwórz kod dla NewCustomer
 Dodaj następujący kod do formularza NewCustomer. Wykonaj kroki poszczególnych bloków kodu, używając numerowanych komentarzy i tabeli po kodzie.

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
|NC-1|Dodaj `System.Data.SqlClient` i `System.Configuration` do listy przestrzeni nazw.|
|NC-2|Zadeklaruj zmienne `parsedCustomerID` i `orderID`, które będą używane później.|
|NC-3|Wywołaj metodę `GetConnectionString`, aby uzyskać parametry połączenia z pliku konfiguracji aplikacji, i Przechowaj wartość w zmiennej ciągu `connstr`.|
|NC-4|Dodaj kod do programu obsługi zdarzeń kliknięcia dla przycisku `btnCreateAccount`.|
|NC 5|Zawiń wywołanie `isCustomerName` wokół kodu zdarzenia kliknięcia, aby `uspNewCustomer` działać tylko wtedy, gdy nazwa klienta jest obecna.|
|NC-6|Utwórz obiekt `SqlConnection` (`conn`) i przekaż parametry połączenia w `connstr`.|
|NC 7|Utwórz obiekt `SqlCommand`, `cmdNewCustomer`.<br /><br /> -Określ `Sales.uspNewCustomer` jako procedurę przechowywaną do uruchomienia.<br />-Użyj właściwości `CommandType`, aby określić, że polecenie jest procedurą składowaną.|
|NC-8|Dodaj `@CustomerName` parametr wejściowy z procedury składowanej.<br /><br /> -Dodaj parametr do kolekcji `Parameters`.<br />-Użyj wyliczenia `SqlDbType`, aby określić typ parametru jako nvarchar (40).<br />-Określ `txtCustomerName.Text` jako źródło.|
|NC-9|Dodaj parametr wyjściowy z procedury składowanej.<br /><br /> -Dodaj parametr do kolekcji `Parameters`.<br />-Użyj `ParameterDirection.Output`, aby zidentyfikować parametr jako dane wyjściowe.|
|NC-10|Dodaj blok try-catch-finally, aby otworzyć połączenie, uruchomić procedurę przechowywaną, obsłużyć wyjątki, a następnie zamknąć połączenie.|
|NC-11|Otwórz połączenie (`conn`), które zostało utworzone w NC-6.|
|NC 12|Użyj metody `ExecuteNonQuery`, aby `cmdNewCustomer` do uruchomienia `Sales.uspNewCustomer` procedury składowanej. Ta procedura składowana uruchamia instrukcję `INSERT`, a nie zapytanie.|
|NC-13|Wartość `@CustomerID` jest zwracana jako wartość tożsamości z bazy danych. Ponieważ jest to liczba całkowita, należy przekonwertować ją na ciąg w celu wyświetlenia go w polu tekstowym **Identyfikator klienta** .<br /><br /> -Zadeklarowano `parsedCustomerID` w NC-2.<br />-Przechowuj wartość `@CustomerID` w `parsedCustomerID` do późniejszego użycia.<br />— Konwertuj zwrócony identyfikator klienta na ciąg i Wstaw go do `txtCustomerID.Text`.|
|NC-14|Na potrzeby tego przykładu Dodaj prostą klauzulę catch (niebędącą jakością produkcyjną).|
|NC 15|Zawsze zamykaj połączenie po zakończeniu korzystania z niego, aby można było je zwolnić do puli połączeń. Zobacz [SQL Servering Connection pooling (ADO.NET)](https://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx).|
|NC-16|Zdefiniuj metodę, aby sprawdzić, czy nazwa klienta jest obecna.<br /><br /> — Jeśli pole tekstowe jest puste, Wyświetl komunikat i zwróć `false`, ponieważ nazwa jest wymagana do utworzenia konta.<br />-Jeśli pole tekstowe nie jest puste, zwróć `true`.|
|NC – 17|Dodaj kod do programu obsługi zdarzeń kliknięcia dla przycisku `btnPlaceOrder`.|
|NC 18|Zawiń wywołanie `isPlaceOrderReady` wokół kodu zdarzenia `btnPlaceOrder_Click`, dzięki czemu `uspPlaceNewOrder` nie zostanie uruchomiona, jeśli wymagane dane wejściowe nie są obecne.|
|NC-19 za poorednictwem NC-25|Te sekcje kodu przypominają kod, który został dodany dla programu obsługi zdarzeń `btnCreateAccount_Click`.<br /><br /> -NC-19. Utwórz obiekt `SqlCommand`, `cmdNewOrder` i określ `Sales.uspPlaceOrder` jako procedurę składowaną.<br />-NC-20 do NC-23 są parametrami wejściowymi procedury składowanej.<br />-NC-24. `@RC` będzie zawierać wartość zwracaną, która jest wygenerowanym IDENTYFIKATORem zamówienia z bazy danych. Kierunek tego parametru jest określany jako `ReturnValue`.<br />-NC-25. Zapisz wartość identyfikatora zamówienia w zmiennej `orderID`, która została zadeklarowana w NC-2, i wyświetl wartość w oknie komunikatu.|
|NC-26|Zdefiniuj metodę, aby sprawdzić, czy identyfikator klienta istnieje i czy kwota została określona w `numOrderAmount`.|
|NC — 27|Wywołaj metodę `ClearForm` w programie obsługi zdarzeń `btnAddAnotherAccount` kliknij.|
|NC — 28|Utwórz metodę `ClearForm`, aby wyczyścić wartości z formularza, jeśli chcesz dodać innego klienta.|
|NC29|Zamknij formularz NewCustomer i zwróć fokus na formularz nawigacji.|

### <a name="fillorcancel-form"></a>Formularz FillOrCancel
 Formularz FillorCancel uruchamia zapytanie w celu zwrócenia zamówienia po wprowadzeniu identyfikatora zamówienia i wybraniu przycisku **Znajdź zamówienie** . Zwrócony wiersz pojawia się w siatce danych tylko do odczytu. Możesz oznaczyć zamówienie jako anulowane (X), jeśli wybierzesz przycisk **Anuluj zamówienie** lub możesz oznaczyć zamówienie jako wypełnione (F), jeśli wybierzesz przycisk **Wypełnij zamówienie** . Jeśli wybierzesz przycisk **Znajdź zamówienie** ponownie, zostanie wyświetlony zaktualizowany wiersz.

#### <a name="create-event-handlers"></a>Tworzenie programów obsługi zdarzeń
 Utwórz puste programy obsługi zdarzeń kliknięcia dla czterech przycisków w formularzu.

#### <a name="create-code-for-fillorcancel"></a>Utwórz kod dla FillOrCancel
 Dodaj następujący kod do formularza FillOrCancel. Przechodzenie między blokami kodu przy użyciu ponumerowanych komentarzy i tabeli, która następuje po kodzie.

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
|FC-1|Dodaj `System.Data.SqlClient`, `System.Configuration` i `System.Text.RegularExpressions` do listy przestrzeni nazw.|
|FC-2|Zadeklaruj zmienną `parsedOrderID`.|
|FC-3|Wywołaj metodę `GetConnectionString`, aby uzyskać parametry połączenia z pliku konfiguracji aplikacji, i Przechowaj wartość w zmiennej ciągu `connstr`.|
|FC 4|Dodaj kod do programu obsługi zdarzeń kliknięcia dla `btnFindOrderByID`.|
|FC-5|Te zadania są wymagane przed podjęciem próby uruchomienia instrukcji SQL lub procedury składowanej.<br /><br /> — Utwórz obiekt `SqlConnection`.<br />-Zdefiniuj instrukcję SQL lub określ nazwę procedury składowanej. (W tym przypadku zostanie uruchomiona instrukcja `SELECT`).<br />— Utwórz obiekt `SqlCommand`.<br />-Zdefiniuj wszystkie parametry instrukcji SQL lub procedury składowanej.|
|FC-6|Ten kod używa `SqlDataReader` i `DataTable` do pobierania i wyświetlania wyników zapytania.<br /><br /> — Otwórz połączenie.<br />-Utwórz obiekt `SqlDataReader`, `rdr`, uruchamiając metodę `ExecuteReader` dla `cmdOrderID`.<br />— Utwórz obiekt `DataTable`, aby przechowywać pobrane dane.<br />— Załaduj dane z obiektu `SqlDataReader` do obiektu `DataTable`.<br />-Wyświetl dane w widoku siatki danych, określając `DataTable` jako `DataSource` dla widoku siatki danych.<br />-Zamknij `SqlDataReader`.|
|FC-7|Dodaj kod do programu obsługi zdarzeń kliknięcia dla `btnCancelOrder`. Ten kod uruchamia `Sales.uspCancelOrder` procedury składowanej.|
|FC-8|Dodaj kod do programu obsługi zdarzeń kliknięcia dla `btnFillOrder`. Ten kod uruchamia `Sales.uspFillOrder` procedury składowanej.|
|FC-9|Utwórz metodę, aby sprawdzić, czy `OrderID` jest gotowa do przesłania jako parametr do obiektu `SqlCommand`.<br /><br /> -Upewnij się, że identyfikator został wprowadzony w `txtOrderID`.<br />-Użyj `Regex.IsMatch`, aby zdefiniować proste sprawdzanie dla znaków niebędących liczbami całkowitymi.<br />— Zadeklarowano zmienną `parsedOrderID` na FC-2.<br />-Jeśli dane wejściowe są prawidłowe, przekonwertuj tekst na liczbę całkowitą i Zapisz wartość w zmiennej `parsedOrderID`.<br />— Zawiń `isOrderID` metodę wokół `btnFindByOrderID`, `btnCancelOrder` i `btnFillOrder` obsługi zdarzeń.|

## <a name="BKMK_testyourapplication"></a>Testowanie aplikacji
 Wybierz klawisz F5, aby skompilować i przetestować aplikację po wprowadzeniu kodu dla każdej procedury obsługi zdarzeń, a następnie po zakończeniu kodowania.
