<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="utf-8">
		<meta http-equiv="X-UA-Compatible" content="IE=edge">
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<title>Address Label Demo - Dymo Printer</title>
		<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" />
		<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
		<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
		<script src="https://cdnjs.cloudflare.com/ajax/libs/knockout/3.4.2/knockout-min.js"></script>
		<script type="text/javascript" src="http://labelwriter.com/software/dls/sdk/js/DYMO.Label.Framework.3.0.js"></script>
		<script type="text/javascript" src="labels.js"></script>
	</head>
	<body>
		<div class="container">
			<h1 class="page-header">Print an Address Label <small>With a Dymo LabelWriter</small></h1>
			<form>
				<div class="form-group">
					<textarea id="address-box" name="address-box" class="form-control" rows="6" disabled="disabled" data-bind="disable: message() !== 'Ready'"></textarea>
				</div>
				<div class="row">
					<div class="col-md-12">
						<div class="btn-toolbar" role="toolbar">				
							<button class="btn btn-primary" onclick="return dymoPrint()"  disabled="disabled" data-bind="disable: message() !== 'Ready'">
								Print label
							</button>
							<button type="reset" class="btn btn-default" disabled="disabled" data-bind="disable: message() !== 'Ready'">
								Clear
							</button>
							<button type="button" class="btn btn-link" data-toggle="modal" data-target="#debugModal">
								<span data-bind="text: message">Loading</span>
							</button>
						</div>
					</div>
				</div>

				<!-- Modal -->
				<div class="modal fade" id="debugModal" tabindex="-1" role="dialog" aria-labelledby="debugModal">
					<div class="modal-dialog" role="document">
						<div class="modal-content">
							<div class="modal-header">
								<button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</span></button>
								<h4 class="modal-title" id="myModalLabel">Printer information</h4>
							</div>
							<div class="modal-body">
								<dl>
									<dt>Environment</dt>
									<dd>Browser supported: <span data-bind="text: browserSupported, visible: environmentChecked()"></span></dd>
									<dd>Dymo framework installed: <span data-bind="text: frameworkInstalled, visible: environmentChecked()"></span></dd>
									<dd>Dymo webservice ready: <span data-bind="text: webServicePresent, visible: environmentChecked()"></span></dd>
									<dt>Printer</dt>
									<dd>Name: <span data-bind="text: printerName, visible: printerChecked()"></span></dd>
									<dd>Connected: <span data-bind="text: printerConnected, visible: printerChecked()"></span></dd>
									<dt>Label</dt>
									<dd>Acquired: <span data-bind="text: lebelaAcquired, visible: lebelAjaxComplete()"></span></dd>
								</dl>
							</div>
							<div class="modal-footer">
								<button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
							</div>
						</div>
					</div>
				</div>

			</form>
		</div>
	</body>
</html>
