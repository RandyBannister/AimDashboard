#### Creting Custom Templates
1. Create below folder structure for your template
```
templates/Example
templates/Example/Controllers/MyController.php
templates/Example/Views/index.blade.php
templates/Example/routes.php
```
2. Define your routes like you normally do in laravel framework
edit templates/example/routes.php
```
Route::get('/index', 'MyController@index');
```
Your new routes will be available as http://dashboard.marmonim.com/t/example/index

3. Minimum Example of MyController definition:

```
<?php
namespace Templates\Example\Controllers;

use Illuminate\Http\Request;
use App\Http\Controllers\Controller;

class MyController extends Controller
{
    public function index()
    {
        return view('Example::index');
    }
}
```

Below example show how to use some additional marmonim functions:

```
<?php
namespace Templates\Example\Controllers;

use Illuminate\Http\Request;
use App\Http\Controllers\Controller;
use App\Libraries\MarmonIm;
use \Session;

class MyController extends Controller
{
 	use MarmonIm;

    public function index($id, Request $request)
    {
        $this->setToken($request);
        $unit = $this->getUnits($id);

        return view('Example::index')->with('unit', $unit)->with('user', Session::get('user'));
    }
}
```
