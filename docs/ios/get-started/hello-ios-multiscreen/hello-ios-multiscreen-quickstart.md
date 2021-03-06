---
title: Hello, iOS Multiscreen
description: En esta guía de dos partes, ampliaremos la aplicación Phoneword creada en la guía Hello, iOS a fin de controlar una segunda pantalla. Además, presentaremos el modelo de diseño Modelo-Vista-Controlador, implementaremos nuestra primera navegación de iOS y conoceremos a fondo la estructura y la funcionalidad de la aplicación iOS.
ms.topic: quickstart
ms.prod: xamarin
ms.assetid: d72e6230-c9ee-4bee-90ec-877d256821aa
ms.technology: xamarin-ios
author: bradumbaugh
ms.author: brumbaug
ms.date: 12/02/2016
ms.openlocfilehash: 3b59b942b3c256418d60436a1c4ba8b4aea14aa4
ms.sourcegitcommit: 945df041e2180cb20af08b83cc703ecd1aedc6b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/04/2018
---
# <a name="helloios-multiscreen-quickstart"></a>Inicio rápido de Multipantalla de Hello, iOS

En esta parte del tutorial se agregará una segunda pantalla a la aplicación Phoneword en que se mostrará un historial de los números de teléfono a los que se llamó con la aplicación. La aplicación final tendrá una segunda pantalla en que se muestra el historial de llamadas, como se ilustra en las capturas de pantalla siguientes:

 [![](hello-ios-multiscreen-quickstart-images/00.png "La aplicación final tiene una segunda pantalla que muestra el historial de llamadas, como se ve en esta captura de pantalla")](hello-ios-multiscreen-quickstart-images/00.png#lightbox)

En el [análisis detallado incluido](~/ios/get-started/hello-ios-multiscreen/hello-ios-multiscreen-deepdive.md), revisaremos la aplicación que se ha creado y explicaremos la arquitectura, la navegación y otros conceptos nuevos de iOS que surjan durante el proceso.

 <a name="Requirements" />

## <a name="requirements"></a>Requisitos

Este guía parte del punto en que se quedó el documento Hello, iOS, y es necesario completar el [Inicio rápido de Hello, iOS](~/ios/get-started/hello-ios/index.md). La versión completa de la aplicación Phoneword se puede descargar en el [Ejemplo de Hello, iOS](https://developer.xamarin.com/samples/monotouch/Hello_iOS/).

# <a name="visual-studio-for-mactabvsmac"></a>[Visual Studio para Mac](#tab/vsmac)

## <a name="walkthrough"></a>Tutorial

En este tutorial se agregará una pantalla Historial de llamadas a nuestra aplicación **Phoneword**.


1. Abra la aplicación **Phoneword** en Visual Studio para Mac. Si es necesario, la aplicación completa de Phoneword de la guía [Tutorial de Hello, iOS](~/ios/get-started/hello-ios/index.md) puede descargarse [aquí](https://developer.xamarin.com/samples/monotouch/Hello_iOS/).


2. Abra el archivo **Main.storyboard** desde el **Panel de solución**:

  ![](hello-ios-multiscreen-quickstart-images/02new.png "Main.storyboard en el Diseñador de iOS")


3. Arrastre un **controlador de navegación** desde el **cuadro de herramientas** a la superficie de diseño (es posible que tenga que reducir el tamaño para ajustarlo todo en la superficie de diseño):

  ![](hello-ios-multiscreen-quickstart-images/03new.png "Arrastre un controlador de navegación desde el cuadro de herramientas a la superficie de diseño")


4. Arrastre el objeto **Sourceless Segue** (que es la flecha gris a la izquierda del controlador de vista única) hasta el **controlador de navegación** para cambiar el punto inicial de la aplicación:

  ![](hello-ios-multiscreen-quickstart-images/04new.png "Arrastre el objeto Sourceless Segue al controlador de navegación para cambiar el punto inicial de la aplicación")


5. Seleccione el **controlador de vista raíz** existente; para ello, haga clic en la barra inferior y pulse **Eliminar** para quitarlo de la superficie de diseño.
A continuación, mueva la escena de **Phoneword** junto al **controlador de navegación**:

  ![](hello-ios-multiscreen-quickstart-images/05new.png "Mueva la escena de Phoneword junto al controlador de navegación")


6. Establezca el **ViewController** como el **controlador de vista raíz** del controlador de navegación. Pulse la tecla **Ctrl** y haga clic dentro del **controlador de navegación**. Debe aparecer una línea azul. A continuación, sin dejar de pulsar la tecla **Ctrl**, arrástrelo desde el **controlador de navegación** a la escena de **Phoneword** y suéltela. Esto se denomina _Ctrl y arrastrar_:

 ![](hello-ios-multiscreen-quickstart-images/06.png "Arrastre desde el controlador de navegación a la escena de Phoneword y suelte")


7. Desde el elemento flotante, establezca la relación con **Raíz**:

  ![](hello-ios-multiscreen-quickstart-images/07new.png "Establecimiento de la relación con Raíz")

  **ViewController** es ahora el **controlador de vista raíz del controlador de navegación:**

  ![](hello-ios-multiscreen-quickstart-images/08.png "ViewController es ahora el controlador de vista raíz del controlador de navegación")


8. Haga doble clic en el barra **Título** de la pantalla **Phoneword** y cambie el **título** por **Phoneword**:

  ![](hello-ios-multiscreen-quickstart-images/09.png "Cambie el título a 'Phoneword'")


9. Arrastre un **botón** desde el **cuadro de herramientas** y colóquelo debajo del **botón Llamada**. Arrastre los controladores para hacer que el **botón** nuevo tenga el mismo ancho que el **botón Llamada**:

  ![](hello-ios-multiscreen-quickstart-images/10new.png "Asegúrese de que el botón nuevo tenga el mismo ancho que el botón Llamada")


10. En el **Panel de propiedades**, cambie el **nombre** del botón por **CallHistoryButton** y cambie el **título** por **Historial de llamadas**:

  ![](hello-ios-multiscreen-quickstart-images/11new.png "Cambie el nombre del botón a CallHistoryButton y el título a Historial de llamadas")


11. Cree la pantalla **Historial de llamadas**. Desde el **Cuadro de herramientas**, arrastre un **controlador de vista de tabla** a la superficie de diseño:

 ![](hello-ios-multiscreen-quickstart-images/12new.png "Arrastre un controlador de vista de tabla a la superficie de diseño")


12. A continuación, haga clic en la barra negra situada en la parte inferior de la escena para seleccionar el **controlador de vista de tabla**. En el **Panel de propiedades**, cambie la clase del **controlador de vista de tabla** por `CallHistoryController` y pulse **Entrar**:

  ![](hello-ios-multiscreen-quickstart-images/13new.png "Cambie la clase del controlador de vista de tabla a CallHistoryController")

  El Diseñador de iOS generará una clase auxiliar personalizada denominada `CallHistoryController` para administrar la jerarquía de la vista de contenido de esta pantalla.
  El archivo **CallHistoryController.cs** aparecerá en el **Panel de solución**:

  ![](hello-ios-multiscreen-quickstart-images/14new.png "Archivo CallHistoryController.cs en el Panel de solución")


13. Haga doble clic en el archivo **CallHistoryController.cs** para abrirlo y reemplace el contenido por el código siguiente:

  ```csharp
  using System;
  using Foundation;
  using UIKit;
  using System.Collections.Generic;

  namespace Phoneword_iOS
  {
      public partial class CallHistoryController : UITableViewController
      {
          public List<string> PhoneNumbers { get; set; }

          static NSString callHistoryCellId = new NSString ("CallHistoryCell");

          public CallHistoryController (IntPtr handle) : base (handle)
          {
              TableView.RegisterClassForCellReuse (typeof(UITableViewCell), callHistoryCellId);
              TableView.Source = new CallHistoryDataSource (this);
              PhoneNumbers = new List<string> ();
          }

          class CallHistoryDataSource : UITableViewSource
          {
              CallHistoryController controller;

              public CallHistoryDataSource (CallHistoryController controller)
              {
                  this.controller = controller;
              }

              public override nint RowsInSection (UITableView tableView, nint section)
              {
                  return controller.PhoneNumbers.Count;
              }

              public override UITableViewCell GetCell (UITableView tableView, NSIndexPath indexPath)
              {
                  var cell = tableView.DequeueReusableCell (CallHistoryController.callHistoryCellId);

                  int row = indexPath.Row;
                  cell.TextLabel.Text = controller.PhoneNumbers [row];
                  return cell;
              }
          }
      }
  }
  ```

  Guarde la aplicación (**⌘ + s**) y compílela (**⌘ + b**) para asegurarse de que no existen errores.


14. Cree un objeto _Segue_ (transición) entre la escena de **Phoneword** y la escena del **Historial de llamadas**.
  En la **escena de Phoneword**, seleccione el **botón Historial de llamadas**, pulse la tecla Ctrl y arrástrelo desde el **botón** a la escena del **Historial de llamadas**:

  ![](hello-ios-multiscreen-quickstart-images/15.png "Pulse CTRL y arrastre desde el botón a la escena de Historial de llamadas")

  En el elemento flotante **Segue de acción**, seleccione **Mostrar**.

  El Diseñador de iOS agregará un objeto Segue entre las dos escenas:

  ![](hello-ios-multiscreen-quickstart-images/17new.png "Segue entre las dos escenas")


15. Agregue un **título** al **controlador de vista de tabla**; para ello, seleccione la barra negra situada en la parte inferior de la escena y cambie el **título del controlador de vista** por **Historial de llamadas** en el **Panel de propiedades**:

  ![](hello-ios-multiscreen-quickstart-images/18new.png "Cambie el título del controlador de vista a Historial de llamadas en el panel Propiedades")

16. Cuando la aplicación se ejecute, el **botón Historial de llamadas** se abrirá en la pantalla **Historial de llamadas**, pero la vista de tabla estará vacía porque no hay ningún código para mostrar los números de teléfono ni del cual realizar un seguimiento.

  Esta aplicación almacenará los números de teléfono como una lista de cadenas.

  Agregue una directiva de `using` para `System.Collections.Generic` en la parte superior de **ViewController**:

  ```csharp
  using System.Collections.Generic;
  ```



17. Modifique la clase de `ViewController` con el código siguiente:

    ```csharp
    using System;
    using System.Collections.Generic;
    using Foundation;
    using UIKit;

    namespace Phoneword_iOS
    {
      public partial class ViewController : UIViewController
      {
        string translatedNumber = "";

        public List<string> PhoneNumbers { get; set; }

        protected ViewController(IntPtr handle) : base(handle)
        {
          //initialize list of phone numbers called for Call History screen
          PhoneNumbers = new List<string>();
        }

        public override void ViewDidLoad()
        {
          base.ViewDidLoad();
          // Perform any additional setup after loading the view, typically from a nib.

          TranslateButton.TouchUpInside += (object sender, EventArgs e) => {
            // Convert the phone number with text to a number
            // using PhoneTranslator.cs
            translatedNumber = PhoneTranslator.ToNumber(
              PhoneNumberText.Text);

            // Dismiss the keyboard if text field was tapped
            PhoneNumberText.ResignFirstResponder();

            if (translatedNumber == "")
            {
              CallButton.SetTitle("Call ", UIControlState.Normal);
              CallButton.Enabled = false;
            }
            else
            {
              CallButton.SetTitle("Call " + translatedNumber,
                UIControlState.Normal);
              CallButton.Enabled = true;
            }
          };

          CallButton.TouchUpInside += (object sender, EventArgs e) => {

            //Store the phone number that we're dialing in PhoneNumbers
            PhoneNumbers.Add(translatedNumber);

            // Use URL handler with tel: prefix to invoke Apple's Phone app...
            var url = new NSUrl("tel:" + translatedNumber);

            // otherwise show an alert dialog
            if (!UIApplication.SharedApplication.OpenUrl(url))
            {
              var alert = UIAlertController.Create("Not supported", "Scheme 'tel:' is not supported on this device", UIAlertControllerStyle.Alert);
              alert.AddAction(UIAlertAction.Create("Ok", UIAlertActionStyle.Default, null));
              PresentViewController(alert, true, null);
            }
          };
        }

        public override void PrepareForSegue(UIStoryboardSegue segue, NSObject sender)
        {
          base.PrepareForSegue(segue, sender);

          // set the View Controller that’s powering the screen we’re
          // transitioning to

          var callHistoryContoller = segue.DestinationViewController as CallHistoryController;

          //set the Table View Controller’s list of phone numbers to the
          // list of dialed phone numbers

          if (callHistoryContoller != null)
          {
            callHistoryContoller.PhoneNumbers = PhoneNumbers;
          }
        }
      }
    }
    ```


Aquí suceden algunas cosas.
  * La variable `translatedNumber` se ha movido desde el método `ViewDidLoad` a una _variable de nivel de clase_.
  * El código **CallButton** se modificó para agregar los números marcados a la lista de números de teléfono mediante una llamada a `PhoneNumbers.Add(translatedNumber)`.
  * Se agregó el método `PrepareForSegue`.

  Guarde y compile la aplicación para asegurarse de que no existen errores.

20. Pulse el botón **Iniciar** para iniciar la aplicación dentro del **Simulador de iOS**:

  ![](hello-ios-multiscreen-quickstart-images/19.png "Pulse el botón Iniciar para iniciar la aplicación dentro del Simulador de iOS")


Enhorabuena por completar su primera aplicación multipantalla de Xamarin.iOS.

# <a name="visual-studiotabvswin"></a>[Visual Studio](#tab/vswin)

## <a name="walkthrough"></a>Tutorial

En este tutorial se agregará una pantalla Historial de llamadas a nuestra aplicación **Phoneword**.


1. Abra la aplicación **Phoneword** en Visual Studio. Si es necesario, la [aplicación completa de Phoneword](https://developer.xamarin.com/samples/monotouch/Hello_iOS/) de la guía [Tutorial de Hello, iOS](~/ios/get-started/hello-ios/index.md) puede descargarse. Recuerde que es necesario conectarse a un equipo [Mac](~/ios/get-started/installation/windows/connecting-to-mac/index.md) para utilizar el Diseñador de iOS y el Simulador de iOS.


2. Empiece por editar la interfaz de usuario. Abra el archivo **Main.storyboard** desde el **Explorador de soluciones** y asegúrese de establecer **Ver como** en _iPhone 6_:

  ![](hello-ios-multiscreen-quickstart-images/image1.png "Main.storyboard en el Diseñador de iOS")


3. Arrastre un **controlador de navegación** desde el **cuadro de herramientas** a la superficie de diseño:

  ![](hello-ios-multiscreen-quickstart-images/image2.png "Arrastre un controlador de navegación desde el cuadro de herramientas a la superficie de diseño")


4. Arrastre el objeto **Sourceless Segue** (que es la flecha gris a la izquierda de la escena de **Phoneword**) desde la escena de **Phoneword** al **controlador de navegación** para cambiar el punto inicial de la aplicación:

  ![](hello-ios-multiscreen-quickstart-images/image3.png "Arrastre el objeto Sourceless Segue al controlador de navegación para cambiar el punto inicial de la aplicación")


5. Haga clic en la barra negra para seleccionar el **controlador de vista raíz** y pulse **Eliminar** para quitarlo de la superficie de diseño.
  A continuación, mueva la escena de **Phoneword** junto al **controlador de navegación**:

  ![](hello-ios-multiscreen-quickstart-images/image4.png "Mueva la escena de Phoneword junto al controlador de navegación")


6. Establezca el **ViewController** como el controlador de navegación de `Root View Controller`. Pulse la tecla **Ctrl** y haga clic dentro del **controlador de navegación**. Debe aparecer una línea azul. A continuación, sin dejar de pulsar la tecla **Ctrl**, arrástrelo desde el **controlador de navegación** a la escena de **Phoneword** y suéltela. Esto se denomina _Ctrl y arrastrar_:

  ![](hello-ios-multiscreen-quickstart-images/image5.png "Arrastre desde el controlador de navegación a la escena de Phoneword y suelte")


7. Desde el elemento flotante, establezca la relación con **Raíz**:

  ![](hello-ios-multiscreen-quickstart-images/image6.png "Establezca la relación con Raíz")

  El **ViewController** es ahora nuestro **controlador de vista raíz del controlador de navegación.**


8. Haga doble clic en el barra **Título** de la pantalla **Phoneword** y cambie el **título** por **Phoneword**:

  ![](hello-ios-multiscreen-quickstart-images/image7.png "Cambie el título a Phoneword")


9. Arrastre un **botón** desde el **cuadro de herramientas** y colóquelo debajo del **botón Llamada**. Arrastre los controladores para hacer que el **botón** nuevo tenga el mismo ancho que el **botón Llamada**:

  ![](hello-ios-multiscreen-quickstart-images/image8.png "Asegúrese de que el botón nuevo tenga el mismo ancho que el botón Llamada")


10. En el **Explorador de propiedades**, cambie el **nombre** del **botón** por `CallHistoryButton` y cambie el **título** por **Historial de llamadas**:

  ![](hello-ios-multiscreen-quickstart-images/image9.png "Cambie el nombre del botón a 'CallHistoryButton' y el título a 'Historial de llamadas'")


11. Cree la pantalla **Historial de llamadas**. Desde el **Cuadro de herramientas**, arrastre un **controlador de vista de tabla** a la superficie de diseño:

  ![](hello-ios-multiscreen-quickstart-images/image10.png "Arrastre un controlador de vista de tabla a la superficie de diseño")


12. Haga clic en la barra negra situada en la parte inferior de la escena para seleccionar el **controlador de vista de tabla**. En el **Explorador de propiedades**, cambie la clase del **controlador de vista de tabla** por `CallHistoryController` y pulse **Entrar**:

  ![](hello-ios-multiscreen-quickstart-images/image11.png "Cambie la clase del controlador de vista de tabla a CallHistoryController")

  El Diseñador de iOS generará una clase auxiliar personalizada denominada `CallHistoryController` para administrar la jerarquía de la vista de contenido de esta pantalla.
  El archivo **CallHistoryController.cs** aparecerá en el **Explorador de soluciones**:

  ![](hello-ios-multiscreen-quickstart-images/image12.png "Archivo CallHistoryController.cs en el Explorador de soluciones")


13. Haga doble clic en el archivo **CallHistoryController.cs** para abrirlo y reemplace el contenido por el código siguiente:

        using System;
        using Foundation;
        using UIKit;
        using System.Collections.Generic;

        namespace Phoneword
        {
            public partial class CallHistoryController : UITableViewController
            {
                public List<String> PhoneNumbers { get; set; }

                static NSString callHistoryCellId = new NSString ("CallHistoryCell");

                public CallHistoryController (IntPtr handle) : base (handle)
                {
                    TableView.RegisterClassForCellReuse (typeof(UITableViewCell), callHistoryCellId);
                    TableView.Source = new CallHistoryDataSource (this);
                    PhoneNumbers = new List<string> ();
                }

                class CallHistoryDataSource : UITableViewSource
                {
                    CallHistoryController controller;

                    public CallHistoryDataSource (CallHistoryController controller)
                    {
                        this.controller = controller;
                    }

                    // Returns the number of rows in each section of the table
                    public override nint RowsInSection (UITableView tableView, nint section)
                    {
                        return controller.PhoneNumbers.Count;
                    }

                    public override UITableViewCell GetCell (UITableView tableView, NSIndexPath indexPath)
                    {
                        var cell = tableView.DequeueReusableCell (CallHistoryController.callHistoryCellId);

                        int row = indexPath.Row;
                        cell.TextLabel.Text = controller.PhoneNumbers [row];
                        return cell;
                    }
                }
            }
        }

  Guarde la aplicación y compílela para asegurarse de que no existen errores. Puede omitir las advertencias de compilación por ahora.


14. Cree un objeto _Segue_ (transición) entre la escena de **Phoneword** y la escena del **Historial de llamadas**.
  En la **escena de Phoneword**, seleccione el **botón Historial de llamadas**, **pulse la tecla Ctrl y arrástrelo** desde el **botón** a la escena del **Historial de llamadas**:

  ![](hello-ios-multiscreen-quickstart-images/image13.png "Pulse CTRL y arrastre desde el botón a la escena de Historial de llamadas")

  En el elemento flotante **Segue de acción**, seleccione **Mostrar**:

  ![](hello-ios-multiscreen-quickstart-images/image14.png "Seleccione Mostrar como tipo de segue")

  El Diseñador de iOS agregará un objeto Segue entre las dos escenas:

  ![](hello-ios-multiscreen-quickstart-images/image15.png "Segue entre las dos escenas")


15. Agregue un **título** al **controlador de vista de tabla**; para ello, seleccione la barra negra situada en la parte inferior de la escena y cambie **Controlador de vista > Título** por **Historial de llamadas** en el **Explorador de propiedades**:

  ![](hello-ios-multiscreen-quickstart-images/image16.png "Cambie el título del controlador de vista a Historial de llamadas")


16. Cuando la aplicación se ejecute, el **botón Historial de llamadas** se abrirá en la pantalla **Historial de llamadas**, pero la vista de tabla estará vacía porque no hay ningún código para mostrar los números de teléfono ni del cual realizar un seguimiento.

  Esta aplicación almacenará los números de teléfono como una lista de cadenas.

  Agregue una directiva de `using` para `System.Collections.Generic` en la parte superior de **ViewController**:

        using System.Collections.Generic;

17. Modifique la clase de `ViewController` con el código siguiente:

    ```csharp
    using System;
    using System.Collections.Generic;
    using Foundation;
    using UIKit;

    namespace Phoneword_iOS
    {
      public partial class ViewController : UIViewController
      {
        string translatedNumber = "";

        public List<string> PhoneNumbers { get; set; }

        protected ViewController(IntPtr handle) : base(handle)
        {
          //initialize list of phone numbers called for Call History screen
          PhoneNumbers = new List<string>();
        }

        public override void ViewDidLoad()
        {
          base.ViewDidLoad();
          // Perform any additional setup after loading the view, typically from a nib.

          TranslateButton.TouchUpInside += (object sender, EventArgs e) => {
            // Convert the phone number with text to a number
            // using PhoneTranslator.cs
            translatedNumber = PhoneTranslator.ToNumber(
              PhoneNumberText.Text);

            // Dismiss the keyboard if text field was tapped
            PhoneNumberText.ResignFirstResponder();

            if (translatedNumber == "")
            {
              CallButton.SetTitle("Call ", UIControlState.Normal);
              CallButton.Enabled = false;
            }
            else
            {
              CallButton.SetTitle("Call " + translatedNumber,
                UIControlState.Normal);
              CallButton.Enabled = true;
            }
          };

          CallButton.TouchUpInside += (object sender, EventArgs e) => {

            //Store the phone number that we're dialing in PhoneNumbers
            PhoneNumbers.Add(translatedNumber);

            // Use URL handler with tel: prefix to invoke Apple's Phone app...
            var url = new NSUrl("tel:" + translatedNumber);

            // otherwise show an alert dialog
            if (!UIApplication.SharedApplication.OpenUrl(url))
            {
              var alert = UIAlertController.Create("Not supported", "Scheme 'tel:' is not supported on this device", UIAlertControllerStyle.Alert);
              alert.AddAction(UIAlertAction.Create("Ok", UIAlertActionStyle.Default, null));
              PresentViewController(alert, true, null);
            }
          };
        }

        public override void PrepareForSegue(UIStoryboardSegue segue, NSObject sender)
        {
          base.PrepareForSegue(segue, sender);

          // set the View Controller that’s powering the screen we’re
          // transitioning to

          var callHistoryContoller = segue.DestinationViewController as CallHistoryController;

          //set the Table View Controller’s list of phone numbers to the
          // list of dialed phone numbers

          if (callHistoryContoller != null)
          {
            callHistoryContoller.PhoneNumbers = PhoneNumbers;
          }
        }
      }
    }
    ```

Aquí suceden algunas cosas.
  * La variable `translatedNumber` se ha movido desde el método `ViewDidLoad` a una _variable de nivel de clase_.
  * El código **CallButton** se modificó para agregar los números marcados a la lista de números de teléfono mediante una llamada a `PhoneNumbers.Add(translatedNumber)`.
  * Se agregó el método `PrepareForSegue`.

  Guarde y compile la aplicación para asegurarse de que no existen errores.

  Guarde y compile la aplicación para asegurarse de que no existen errores.


20. Pulse el botón **Iniciar** para iniciar nuestra aplicación dentro del **Simulador de iOS**:

  ![](hello-ios-multiscreen-quickstart-images/19.png "Primera pantalla de la aplicación de ejemplo")


Enhorabuena por completar su primera aplicación multipantalla de Xamarin.iOS.


-----

La aplicación ahora puede controlar la navegación con ambos objetos Segue de guión gráfico y mediante el código. Ahora es el momento de analizar minuciosamente las herramientas y los conocimientos que acaba de aprender en el [Análisis detallado de Multipantalla de Hello, Android](~/ios/get-started/hello-ios-multiscreen/hello-ios-multiscreen-deepdive.md).


## <a name="related-links"></a>Vínculos relacionados

- [Hola, iOS (ejemplo)](https://developer.xamarin.com/samples/monotouch/Hello_iOS/)
- [Directrices de la interfaz humana de iOS](http://developer.apple.com/library/ios/#documentation/UserExperience/Conceptual/MobileHIG/Introduction/Introduction.html)
- [Portal de aprovisionamiento de iOS](https://developer.apple.com/ios/manage/overview/index.action)
