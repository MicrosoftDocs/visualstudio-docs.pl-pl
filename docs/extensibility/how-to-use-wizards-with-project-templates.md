---
title: 'Porady: korzystanie z kreatora z szablonami projektu'
description: Dowiedz się, jak używać interfejsu IWizard w zestawie SDK programu Visual Studio, który umożliwia uruchamianie kodu niestandardowego, gdy użytkownik tworzy projekt na podstawie szablonu.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21e0e35b43fc3b94a8d029c97f56bd573ebac95f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996373"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Instrukcje: korzystanie z kreatorów z szablonami projektu

Program Visual Studio udostępnia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejs, który po zaimplementowaniu umożliwia uruchamianie kodu niestandardowego, gdy użytkownik tworzy projekt na podstawie szablonu.

Dostosowanie szablonu projektu może służyć do wyświetlania niestandardowego interfejsu użytkownika, który gromadzi dane wprowadzane przez użytkownika w celu dostosowania szablonu, dodania dodatkowych plików do szablonu lub dowolnej innej akcji dozwolonej w projekcie.

<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>Metody interfejsu są wywoływane w różnym czasie podczas tworzenia projektu, zaczynając od razu po kliknięciu przycisku **OK** w oknie dialogowym **Nowy projekt** . Każda metoda interfejsu ma nazwę do opisania punktu, w którym jest wywoływana. Na przykład program Visual Studio wywołuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> natychmiast po rozpoczęciu tworzenia projektu, dzięki czemu jest dobrym miejscem do pisania kodu niestandardowego do zbierania danych wejściowych użytkownika.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Tworzenie projektu szablonu projektu z projektem VSIX

Utwórz szablon niestandardowy z projektem szablonu projektu, który jest częścią zestawu Visual Studio SDK. W tej procedurze użyjemy projektu szablonu projektu C#, ale istnieje również Visual Basic projektu szablonu projektu. Następnie należy dodać projekt VSIX do rozwiązania, które zawiera projekt szablonu projektu.

1. Utwórz projekt szablonu projektu C# (w programie Visual Studio wybierz pozycję **plik**  >  **Nowy**  >  **projekt** i wyszukaj "szablon projektu"). Nadaj mu nazwę **MyProjectTemplate**.

   > [!NOTE]
   > Może zostać wyświetlony monit o zainstalowanie zestawu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

2. Dodaj nowy projekt VSIX w tym samym rozwiązaniu co projekt szablonu projektu (w **Eksplorator rozwiązań** wybierz węzeł rozwiązania, kliknij prawym przyciskiem myszy, a następnie wybierz pozycję **Dodaj**  >  **Nowy projekt** i wyszukaj ciąg "VSIX"). Nadaj mu nazwę **MyProjectWizard.**

3. Ustaw projekt VSIX jako projekt startowy. W **Eksplorator rozwiązań** wybierz węzeł projektu VSIX, kliknij prawym przyciskiem myszy, a następnie wybierz pozycję **Ustaw jako projekt startowy**.

4. Dodaj projekt szablonu jako element zawartości projektu VSIX. W **Eksplorator rozwiązań** w WĘŹLE projekt VSIX Znajdź plik *source. Extension. vsixmanifest* . Kliknij go dwukrotnie, aby otworzyć go w edytorze manifestu.

5. W edytorze manifestu wybierz kartę **zasoby** po lewej stronie okna.

6. Na karcie **zasoby** wybierz pozycję **Nowy**. W oknie **Dodawanie nowego zasobu** dla pola Typ wybierz **Microsoft. VisualStudio. ProjectTemplate**. W polu **Źródło** wybierz **projekt w bieżącym rozwiązaniu**. W polu **projekt** wybierz pozycję **MyProjectTemplate**. Następnie kliknij przycisk **OK**.

7. Skompiluj rozwiązanie i Rozpocznij debugowanie. Zostanie wyświetlone drugie wystąpienie programu Visual Studio. (Może to potrwać kilka minut).

8. W drugim wystąpieniu programu Visual Studio spróbuj utworzyć nowy projekt z nowym szablonem (**plik**  >  **Nowy**  >  **projekt**, wyszukaj ciąg "Moje projekty"). Nowy projekt powinien pojawić się z klasą o nazwie **Class1**. Szablon projektu niestandardowego został utworzony. Zatrzymaj debugowanie teraz.

## <a name="create-a-custom-template-wizard"></a>Kreator tworzenia szablonu niestandardowego

Ta procedura pokazuje, jak utworzyć Kreatora niestandardowego, który otwiera formularz systemu Windows przed utworzeniem projektu. Formularz umożliwia użytkownikom dodanie wartości parametru niestandardowego, która jest dodawana do kodu źródłowego podczas tworzenia projektu.

1. Skonfiguruj projekt VSIX, aby umożliwić mu Tworzenie zestawu.

2. W **Eksplorator rozwiązań** wybierz węzeł projektu VSIX. Poniżej **Eksplorator rozwiązań** powinien zostać wyświetlony okno **Właściwości** . Jeśli tego nie zrobisz, wybierz pozycję **Wyświetl**  >  **okno właściwości** lub naciśnij klawisz **F4**. W oknie **Właściwości** wybierz następujące pola, aby `true` :

   - **Dołącz zestaw do kontenera VSIX**

   - **Dołącz symbole debugowania w kontenerze VSIX**

   - **Dołącz symbole debugowania do lokalnego wdrożenia VSIX**

3. Dodaj zestaw jako element zawartości do projektu VSIX. Otwórz plik *source. Extension. vsixmanifest* i wybierz kartę **Assets (zasoby** ). W oknie **Dodawanie nowego elementu zawartości** dla pozycji **Typ** wybierz pozycję **Microsoft. VisualStudio. Assembly**, w polu **Źródło** wybierz **projekt w bieżącym rozwiązaniu**, a następnie wybierz pozycję **Project** SELECT **MyProjectWizard**.

4. Dodaj następujące odwołania do projektu VSIX. (W **Eksplorator rozwiązań** w WĘŹLE projekt VSIX wybierz pozycję **odwołania**, kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Dodaj odwołanie**.) W oknie dialogowym **Dodawanie odwołania** na karcie **Struktura** znajdź zestaw **System. Windows Forms** i wybierz go. Znajdź również i wybierz zestawy **systemowe** i **System. Drawing** . Teraz wybierz kartę **rozszerzenia** . Znajdź zestaw **EnvDTE** i wybierz go. Znajdź również zestaw **Microsoft. VisualStudio. TemplateWizardInterface** i wybierz go. Kliknij przycisk **OK**.

5. Dodaj klasę dla implementacji kreatora do projektu VSIX. (W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł projektu VSIX i wybierz polecenie **Dodaj**, następnie **nowy element**, a następnie **klasy**.) Nadaj klasie nazwę **WizardImplementation**.

6. Zastąp kod w pliku *WizardImplementationClass.cs* następującym kodem:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.TemplateWizard;
   using System.Windows.Forms;
   using EnvDTE;

   namespace MyProjectWizard
   {
       public class WizardImplementation:IWizard
       {
           private UserInputForm inputForm;
           private string customMessage;

           // This method is called before opening any item that
           // has the OpenInEditor attribute.
           public void BeforeOpeningFile(ProjectItem projectItem)
           {
           }

           public void ProjectFinishedGenerating(Project project)
           {
           }

           // This method is only called for item templates,
           // not for project templates.
           public void ProjectItemFinishedGenerating(ProjectItem
               projectItem)
           {
           }

           // This method is called after the project is created.
           public void RunFinished()
           {
           }

           public void RunStarted(object automationObject,
               Dictionary<string, string> replacementsDictionary,
               WizardRunKind runKind, object[] customParams)
           {
               try
               {
                   // Display a form to the user. The form collects
                   // input for the custom message.
                   inputForm = new UserInputForm();
                   inputForm.ShowDialog();

                   customMessage = UserInputForm.CustomMessage;

                   // Add custom parameters.
                   replacementsDictionary.Add("$custommessage$",
                       customMessage);
               }
               catch (Exception ex)
               {
                   MessageBox.Show(ex.ToString());
               }
           }

           // This method is only called for item templates,
           // not for project templates.
           public bool ShouldAddProjectItem(string filePath)
           {
               return true;
           }
       }
   }
   ```

    **UserInputForm** przywoływany w tym kodzie zostanie zaimplementowana później.

    `WizardImplementation`Klasa zawiera implementacje metod dla każdego elementu członkowskiego <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> . W tym przykładzie tylko <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Metoda wykonuje zadanie. Wszystkie inne metody nie wykonują żadnej operacji ani nie zwracają `true` .

    <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>Metoda przyjmuje cztery parametry:

   - <xref:System.Object>Parametr, który może być rzutowany na <xref:EnvDTE._DTE> obiekt główny, aby umożliwić dostosowanie projektu.

   - <xref:System.Collections.Generic.Dictionary%602>Parametr, który zawiera kolekcję wszystkich wstępnie zdefiniowanych parametrów w szablonie. Aby uzyskać więcej informacji na temat parametrów szablonu, zobacz [Parametry szablonu](../ide/template-parameters.md).

   - <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind>Parametr, który zawiera informacje o rodzaju używanego szablonu.

   - <xref:System.Object>Tablica zawierająca zestaw parametrów przesłanych do kreatora przez program Visual Studio.

     Ten przykład dodaje wartość parametru z formularza danych wejściowych użytkownika do <xref:System.Collections.Generic.Dictionary%602> parametru. Każde wystąpienie `$custommessage$` parametru w projekcie zostanie zastąpione tekstem wprowadzonym przez użytkownika.

7. Teraz Utwórz **UserInputForm**. W pliku *WizardImplementation.cs* Dodaj następujący kod po zakończeniu `WizardImplementation` klasy.

   ```csharp
   public partial class UserInputForm : Form
       {
           private static string customMessage;
           private TextBox textBox1;
           private Button button1;

           public UserInputForm()
           {
               this.Size = new System.Drawing.Size(155, 265);

               button1 = new Button();
               button1.Location = new System.Drawing.Point(90, 25);
               button1.Size = new System.Drawing.Size(50, 25);
               button1.Click += button1_Click;
               this.Controls.Add(button1);

               textBox1 = new TextBox();
               textBox1.Location = new System.Drawing.Point(10, 25);
               textBox1.Size = new System.Drawing.Size(70, 20);
               this.Controls.Add(textBox1);
           }
           public static string CustomMessage
           {
               get
               {
                   return customMessage;
               }
               set
               {
                   customMessage = value;
               }
           }
           private void button1_Click(object sender, EventArgs e)
           {
               customMessage = textBox1.Text;
               this.Close();
           }
       }
   ```

    Formularz dane wejściowe użytkownika zawiera prosty formularz do wprowadzania parametru niestandardowego. Formularz zawiera pole tekstowe o nazwie `textBox1` i przycisk o nazwie `button1` . Gdy przycisk zostanie kliknięty, tekst w polu tekstowym jest przechowywany w `customMessage` parametrze.

## <a name="connect-the-wizard-to-the-custom-template"></a>Połącz kreatora z szablonem niestandardowym

Aby niestandardowy szablon projektu mógł korzystać z niestandardowego kreatora, należy podpisać zestaw kreatora i dodać kilka wierszy do niestandardowego szablonu projektu, aby wiedzieć, gdzie znaleźć implementację kreatora podczas tworzenia nowego projektu.

1. Podpisz zestaw. W **Eksplorator rozwiązań** wybierz projekt VSIX, kliknij prawym przyciskiem myszy, a następnie wybierz **właściwości projektu**.

2. W oknie **właściwości projektu** wybierz kartę **podpisywanie** . na karcie **podpisywanie** zaznacz pozycję **podpisz zestaw**. W polu **Wybierz plik klucza o silnej nazwie** wybierz opcję **\<New>** . W oknie **Tworzenie klucza o silnej nazwie** w polu **Nazwa pliku klucza** wpisz polecenie **Key. snk**. Usuń zaznaczenie pola **Chroń mój klucz przy użyciu hasła** .

3. W **Eksplorator rozwiązań** wybierz projekt VSIX i Znajdź okno **Właściwości** .

4. W polu **Kopiuj dane wyjściowe kompilacji do katalogu wyjściowego** Ustaw **wartość true**. Dzięki temu zestaw będzie kopiowany do katalogu wyjściowego, gdy rozwiązanie zostanie odbudowane. Nadal znajduje się w `.vsix` pliku. Aby można było znaleźć swój klucz podpisywania, należy wyświetlić zestaw.

5. Ponownie skompiluj rozwiązanie.

6. Teraz można znaleźć plik Key. snk w katalogu projektu MyProjectWizard (*\<your disk location> \MyProjectTemplate\MyProjectWizard\key.snk*). Skopiuj plik *Key. snk* .

7. Przejdź do katalogu wyjściowego i Znajdź zestaw (*\<your disk location> \ MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll*). Wklej tutaj plik *Key. snk* . (Nie jest to bezwzględnie konieczne, ale ułatwia wykonywanie następujących czynności).

8. Otwórz okno polecenia i przejdź do katalogu, w którym został utworzony zestaw.

9. Znajdź narzędzie do podpisywania *sn.exe* . Na przykład w systemie operacyjnym Windows 10 64-bitowym typowym ścieżką będzie:

     *C:\Program Files (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools*

     Jeśli nie możesz znaleźć tego narzędzia, spróbuj uruchomić polecenie, **gdzie/r. sn.exe** w oknie poleceń. Zanotuj ścieżkę.

10. Wyodrębnij klucz publiczny z pliku *Key. snk* . W oknie polecenia wpisz

     **\<location of sn.exe>\sn.exe-p Key. snk plik. Key.**

     Nie zapomnij umieścić ścieżki *sn.exe* ze znakami cudzysłowu, jeśli nazwy katalogów są spacjami.

11. Pobierz token klucza publicznego z pliku:

     **\<location of sn.exe>\sn.exe-t plik. Key.**

     Ponownie nie zapomnij cudzysłowu. W danych wyjściowych powinna zostać wyświetlona linia, taka jak ta

     **Token klucza publicznego to \<token>**

     Zanotuj tę wartość.

12. Dodaj odwołanie do kreatora niestandardowego do pliku *vstemplate* szablonu projektu. W **Eksplorator rozwiązań** Znajdź plik o nazwie *MyProjectTemplate. vstemplate* i otwórz go. Po zakończeniu \<TemplateContent> sekcji Dodaj następującą sekcję:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Gdzie **MyProjectWizard** jest nazwą zestawu, a **token** jest tokenem skopiowanym w poprzednim kroku.

13. Zapisz wszystkie pliki w projekcie i Skompiluj ponownie.

## <a name="add-the-custom-parameter-to-the-template"></a>Dodawanie parametru niestandardowego do szablonu

W tym przykładzie projekt używany jako szablon wyświetla komunikat określony w formularzu danych wejściowych użytkownika Kreatora niestandardowego.

1. W **Eksplorator rozwiązań** przejdź do projektu **MyProjectTemplate** i Otwórz *Class1.cs*.

2. W `Main` metodzie aplikacji Dodaj następujący wiersz kodu.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Parametr `$custommessage$` jest zastępowany tekstem wprowadzonym w formularzu wejściowym użytkownika podczas tworzenia projektu na podstawie szablonu.

W tym miejscu znajduje się pełen plik kodu przed jego wyeksportowaniem do szablonu.

```csharp
using System;
using System.Collections.Generic;
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;
$endif$using System.Text;

namespace $safeprojectname$
{
    public class Class1
    {
          static void Main(string[] args)
          {
               Console.WriteLine("$custommessage$");
          }
    }
}
```

## <a name="use-the-custom-wizard"></a>Korzystanie z Kreatora niestandardowego

Teraz można utworzyć projekt na podstawie szablonu i użyć Kreatora niestandardowego.

1. Skompiluj ponownie rozwiązanie i Rozpocznij debugowanie. Powinno zostać wyświetlone drugie wystąpienie programu Visual Studio.

2. Utwórz nowy projekt MyProjectTemplate. (**Plik**  >  **Nowe**  >  **Projekt**).

3. W oknie dialogowym **Nowy projekt** Wyszukaj ciąg "mój projekt", aby zlokalizować szablon, wpisz nazwę i kliknij przycisk **OK**.

     Zostanie otwarty formularz dane wejściowe użytkownika kreatora.

4. Wpisz wartość parametru niestandardowego i kliknij przycisk.

     Formularz wprowadzania użytkownika kreatora zostanie zamknięty, a projekt zostanie utworzony na podstawie szablonu.

5. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik kodu źródłowego i kliknij polecenie **Wyświetl kod**.

     Należy zauważyć, że został `$custommessage$` zastąpiony tekstem wprowadzonym w formularzu danych wejściowych użytkownika kreatora.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [WizardExtension —, element (szablony Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Pakiety NuGet w szablonach programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
