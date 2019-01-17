---
id: version-1.0.0-modal
title: Modal
sidebar_label: Modal
original_id: modal
---

```html
<form [formGroup]="fisTributacaoForm" (ngSubmit)="save()">
	<div class="modal-default">
		<mat-tab-group mat-stretch-tabs [(selectedIndex)]="selectedIndex" color="primary">
			<mat-tab>
				<ng-template mat-tab-label>CADASTRO DE TRIBUTAÇÃO</ng-template>
				<div class="modal-tab-container">
					<div fxLayout="column" fxLayoutAlign="center">
						<div fxLayout="row wrap" fxLayoutGap="20px grid" fxLayoutAlign="end center" style="padding-right: 10px; padding-bottom: 20px;">
							<mat-slide-toggle id="utilizaEcf" labelPosition="before" color="primary" [attr.disabled]="!utilizaEcf" class="mat-toggle-padding"
							 [(ngModel)]="utilizaEcfChecked" formControlName="utilizaEcfModalFormControl" [formControl]="fisTributacaoForm.controls.utilizaEcfModalFormControl">
								Utiliza na ECF?</mat-slide-toggle>
						</div>
						<div fxLayout="row wrap" fxLayoutGap="20px grid">
							<mat-form-field fxFlex>
								<input [defaultValue] trim="blur" type="text" maxlength="100" autocomplete="off" required id="descricao"
								 matInput placeholder="Descrição do Tributacao" #descricaoModalFormControl (change)="fisTributacaoForm.controls.descricaoModalFormControl.setValue(descricaoModalFormControl.value, {emitEvent: false})"
								 tbindex="0" formControlName="descricaoModalFormControl" [formControl]="fisTributacaoForm.controls.descricaoModalFormControl">
								<mat-error *ngIf="fisTributacaoForm.controls.descricaoModalFormControl.hasError('required')">
									<strong>*</strong>
								</mat-error>
							</mat-form-field>
							<mat-form-field fxFlex>
								<mat-select placeholder="Tipo Tributo" id="tipoTributo" required [formControl]="fisTributacaoForm.controls.tipoTributoModalFormControl"
								 (selectionChange)="setLockTipoOperacao(fisTributacaoForm.controls.tipoTributoModalFormControl.value)">
									<mat-option></mat-option>
									<mat-option *ngFor=" let tipoTributo of lstTipoTributo" [value]="tipoTributo.value">{{tipoTributo.viewValue}}</mat-option>
								</mat-select>
							</mat-form-field>
							<input [defaultValue] type="hidden" tbindex="0" formControlName="tipoTributoHiddenModalFormControl" required
							 [formControl]="fisTributacaoForm.controls.tipoTributoHiddenModalFormControl">
							<mat-form-field fxFlex>
								<mat-select placeholder="Movimento" id="entradaSaida" required (selectionChange)="setLockFieldCST()"
								 [formControl]="fisTributacaoForm.controls.entradaSaidaModalFormControl">
									<mat-option></mat-option>
									<mat-option *ngFor=" let entradaSaida of lstEntradaSaida" [value]="entradaSaida.value">{{entradaSaida.viewValue}}</mat-option>
								</mat-select>
							</mat-form-field>
							<input [defaultValue] type="hidden" tbindex="0" formControlName="entradaSaidaHiddenModalFormControl" required
							 [formControl]="fisTributacaoForm.controls.entradaSaidaHiddenModalFormControl">
							<mat-form-field fxFlex>
								<input [defaultValue] trim="blur" type="text" autocomplete="off" required (click)="openDialogCST()" readonly id="idCST"
								 matInput placeholder="CST" #idCSTModalFormControl (change)="fisTributacaoForm.controls.idCSTModalFormControl.setValue(idCSTModalFormControl.value, {emitEvent: false})"
								 tbindex="0" formControlName="idCSTModalFormControl" [formControl]="fisTributacaoForm.controls.idCSTModalFormControl">
								<mat-icon matSuffix *ngIf="this.fisTributacaoForm.enabled && this.fisTributacaoForm.controls.idCSTModalFormControl.enabled" inline class="material-icons-cadastro hover-yellow" (click)="limparCampo(fisTributacaoForm.controls.idCSTModalFormControl);
                                                                                                                                                         limparCampo(fisTributacaoForm.controls.idCSTHiddenModalFormControl);
                                                                                                                                                         limparCampo(fisTributacaoForm.controls.enquadramentoIPIModalFormControl)">clear</mat-icon>
								<mat-icon matSuffix *ngIf="this.fisTributacaoForm.enabled && this.fisTributacaoForm.controls.idCSTModalFormControl.enabled" inline class="material-icons-cadastro hover-primary" (click)="openDialogCST()">search</mat-icon>
								<mat-error *ngIf="fisTributacaoForm.controls.idCSTModalFormControl.hasError('required')">
									<strong>*</strong>
								</mat-error>
							</mat-form-field>
							<input [defaultValue] type="hidden" [formControl]="fisTributacaoForm.controls.idCSTHiddenModalFormControl">

							<mat-form-field fxFlex>
								<input [defaultValue] currencyMask [(ngModel)]="aliquota" maxlength="6" autocomplete="off" id="aliquota"
								 matInput placeholder="Aliq.Efetiva" tbindex="0" formControlName="aliquotaModalFormControl" [formControl]="fisTributacaoForm.controls.aliquotaModalFormControl">
							</mat-form-field>
							<mat-form-field fxFlex>
								<input [defaultValue] currencyMask [(ngModel)]="aliquotaMajorada" maxlength="6" autocomplete="off" id="aliquotaMajorada"
								 matInput placeholder="Aliq.Majorada" tbindex="0" formControlName="aliquotaMajoradaModalFormControl"
								 [formControl]="fisTributacaoForm.controls.aliquotaMajoradaModalFormControl">
							</mat-form-field>
							<mat-form-field fxFlex>
								<input [defaultValue] currencyMask [(ngModel)]="aliquotaReduzida" maxlength="6" autocomplete="off" id="aliquotaReduzida"
								 matInput placeholder="Aliq.Reduzida" tbindex="0" formControlName="aliquotaReduzidaModalFormControl"
								 [formControl]="fisTributacaoForm.controls.aliquotaReduzidaModalFormControl">
							</mat-form-field>
							<mat-form-field fxFlex>
								<input [defaultValue] trim="blur" type="text" maxlength="3" autocomplete="off" id="csosn" matInput placeholder="CSOSN"
								 tbindex="0" formControlName="csosnModalFormControl" #csosnModalFormControl (change)="fisTributacaoForm.controls.csosnModalFormControl.setValue(csosnModalFormControl.value, {emitEvent: false})"
								 [formControl]="fisTributacaoForm.controls.csosnModalFormControl">
								<mat-error *ngIf="fisTributacaoForm.controls.csosnModalFormControl.hasError('required')">
									<strong>{{msgCampoObrigatorio}}</strong>
								</mat-error>
								<mat-error *ngIf="fisTributacaoForm.controls.csosnModalFormControl.hasError('maxlength')">
									<strong>{{msgCampoMaximoCaracter}}</strong>
								</mat-error>
								<mat-error *ngIf="fisTributacaoForm.controls.csosnModalFormControl.hasError('minlength')">
									<strong>{{msgCampoMinimoCaracter}}</strong>
								</mat-error>
							</mat-form-field>

							<mat-form-field fxFlex>
								<input [defaultValue] currencyMask [(ngModel)]="aliquotaAntecipacaoIcms" maxlength="6" autocomplete="off" id="aliquotaAntecipacaoIcms"
								 matInput placeholder="Aliq.Antecipação" tbindex="0" formControlName="aliquotaAntecipacaoIcmsModalFormControl"
								 [formControl]="fisTributacaoForm.controls.aliquotaAntecipacaoIcmsModalFormControl">
							</mat-form-field>
							<mat-form-field fxFlex>
								<input [defaultValue] trim="blur" type="text" maxlength="4" autocomplete="off" id="enquadramentoIPI" matInput
								 placeholder="Cód.Enquad.IPI" #enquadramentoIPIModalFormControl (change)="fisTributacaoForm.controls.enquadramentoIPIModalFormControl.setValue(enquadramentoIPIModalFormControl.value, {emitEvent: false});setLockCST();"
								 tbindex="0" formControlName="enquadramentoIPIModalFormControl" [formControl]="fisTributacaoForm.controls.enquadramentoIPIModalFormControl">
								<mat-hint>{{hintEnquadramentoIpi}}</mat-hint>
							</mat-form-field>
							<mat-form-field fxFlex>
								<input [defaultValue] trim="blur" type="text" maxlength="2" autocomplete="off" id="naturezaBaseCredito"
								 matInput placeholder="Nat.Base Créd." #naturezaBaseCreditoModalFormControl (change)="fisTributacaoForm.controls.naturezaBaseCreditoModalFormControl.setValue(naturezaBaseCreditoModalFormControl.value, {emitEvent: false})"
								 tbindex="0" formControlName="naturezaBaseCreditoModalFormControl" [formControl]="fisTributacaoForm.controls.naturezaBaseCreditoModalFormControl">
							</mat-form-field>
							<mat-form-field fxFlex>
								<input [defaultValue] trim="blur" type="text" maxlength="8" autocomplete="off" id="receitaPisCofins" matInput
								 placeholder="Cód.Receita" #receitaPisCofinsModalFormControl (change)="fisTributacaoForm.controls.receitaPisCofinsModalFormControl.setValue(receitaPisCofinsModalFormControl.value, {emitEvent: false})"
								 tbindex="0" formControlName="receitaPisCofinsModalFormControl" [formControl]="fisTributacaoForm.controls.receitaPisCofinsModalFormControl">
							</mat-form-field>

							<mat-form-field fxFlex>
								<mat-select placeholder="Tipo de Crédito" id="idCreditoTipo" [formControl]="fisTributacaoForm.controls.idCreditoTipoModalFormControl">
									<mat-option *ngFor=" let creditoTipo of lstCreditoTipo" [value]="creditoTipo.value">{{creditoTipo.viewValue}}</mat-option>
								</mat-select>
							</mat-form-field>
						</div>
					</div>
				</div>
			</mat-tab>
			<mat-tab *ngIf='utilizaEcfChecked'>
				<ng-template mat-tab-label>CADASTRO DE ECF</ng-template>
				<div class="modal-tab-container">
					<div fxLayout="column" fxLayoutAlign="center">
						<div fxLayout="row wrap" class="div-form-fields-before-table" fxLayoutGap="20px grid">
							<mat-form-field fxFlex>
								<input [defaultValue] trim="blur" type="text" autocomplete="off" (click)="openDialogAutomacao()" readonly id="idAutomacao"
								 matInput placeholder="Automação" [formControl]="fisTributacaoForm.controls.idAutomacaoModalFormControl">
								<mat-icon matSuffix *ngIf="this.fisTributacaoForm.enabled" inline class="material-icons-cadastro hover-yellow" (click)="limparCampo(fisTributacaoForm.controls.idAutomacaoModalFormControl);
                                                                                                                                                         limparCampo(fisTributacaoForm.controls.idAutomacaoHiddenModalFormControl)">clear</mat-icon>
								<mat-icon matSuffix *ngIf="this.fisTributacaoForm.enabled" inline class="material-icons-cadastro hover-primary" (click)="openDialogAutomacao()">search</mat-icon>
							</mat-form-field>
							<input [defaultValue] type="hidden" [formControl]="fisTributacaoForm.controls.idAutomacaoHiddenModalFormControl">
							<mat-form-field fxFlex>
								<input [defaultValue] trim="blur" type="text" maxlength="4" autocomplete="off" id="registradorECF" matInput
								 placeholder="Registrador ECF" #registradorECFModalFormControl (change)="fisTributacaoForm.controls.registradorECFModalFormControl.setValue(registradorECFModalFormControl.value, {emitEvent: false})"
								 [formControl]="fisTributacaoForm.controls.registradorECFModalFormControl">
							</mat-form-field>
							<div fxLayout fxFlex="100" fxLayoutAlign="start center">
								<button type="button" mat-raised-button color="primary" class="btn-add-modal" (click)="addECF()">Adicionar</button>
							</div>
						</div>

						<div fxLayout="column">
							<ng-template #loadingScreenfisTributacaoECF>
								<mat-progress-spinner mode="indeterminate" style="margin:0 auto;" [strokeWidth]="1" [diameter]="32" [color]="'green'"></mat-progress-spinner>
							</ng-template>
							<div fxLayout="column" fxLayoutAlign="space-between" *ngIf='dataSourceFisTributacaoECF; else loadingScreenfisTributacaoECF;'>
								<table mat-table #table [dataSource]="dataSourceFisTributacaoECF" class="table table-responsive table-striped table-hover">

									<ng-container matColumnDef="idAutomacao">
										<th mat-header-cell *matHeaderCellDef style="text-align: center;"> Código
										</th>
										<td mat-cell *matCellDef="let fisTributacaoECF" style="text-align: center;">
											{{fisTributacaoECF.idAutomacao}}
										</td>
									</ng-container>

									<ng-container matColumnDef="descricao">
										<th mat-header-cell *matHeaderCellDef style="text-align: center;"> Automação
										</th>
										<td mat-cell *matCellDef="let fisTributacaoECF" style="text-align: left;">
											{{fisTributacaoECF.tbFisAutomacao.descricao}}
										</td>
									</ng-container>

									<ng-container matColumnDef="registradorECF">
										<th mat-header-cell *matHeaderCellDef> Registrador
											ECF
										</th>
										<td mat-cell *matCellDef="let fisTributacaoECF">
											{{fisTributacaoECF.registradorECF}}
										</td>
									</ng-container>

									<ng-container matColumnDef="acao">
										<th mat-header-cell *matHeaderCellDef> Ações
										</th>
										<td mat-cell *matCellDef="let fisTributacaoECF">
											<button mat-icon-button class="table-action hover-danger" data-toggle="modal" (click)="deleteECF(fisTributacaoECF);">
												<mat-icon matTooltip="Apagar" style="cursor: pointer" data-toggle="modal">delete</mat-icon>
											</button>
										</td>
									</ng-container>

									<tr mat-header-row *matHeaderRowDef="displayedColumnsFisTributacaoECF"></tr>
									<tr mat-row *matRowDef="let row; columns: displayedColumnsFisTributacaoECF;"></tr>
								</table>
								<mat-paginator [length]="totalPagina" [pageSize]="registroPorPagina"
								 [pageSizeOptions]="pageSizeOptions" (page)="pageEvent = $event;loadGrid(pageEvent,'P');">
								</mat-paginator>
							</div>
						</div>
						<!--/.col-->
					</div>
				</div>
			</mat-tab>
		</mat-tab-group>
		<div fxLayout="row" fxLayoutAlign="space-between center" fxLayoutGap="20px grid">
			<div fxFlex>
				<p>{{title}}</p>
			</div>
			<div fxFlex fxLayout="row" fxLayoutAlign="end center" fxLayoutGap="8px">
				<button type="button" mat-stroked-button [disabled]="loading" (click)="confirmFechar();">{{
					this.fisTributacaoForm.disabled ? 'Fechar' : 'Cancelar' }}</button>
				<button *hasPermission="[this.fisTributacaoForm.disabled,[9],[2,3]]" [disabled]="loading" mat-flat-button color="primary">
					Salvar</button>
				<img *ngIf="loading" src="data:image/gif;base64,R0lGODlhEAAQAPIAAP///wAAAMLCwkJCQgAAAGJiYoKCgpKSkiH/C05FVFNDQVBFMi4wAwEAAAAh/hpDcmVhdGVkIHdpdGggYWpheGxvYWQuaW5mbwAh+QQJCgAAACwAAAAAEAAQAAADMwi63P4wyklrE2MIOggZnAdOmGYJRbExwroUmcG2LmDEwnHQLVsYOd2mBzkYDAdKa+dIAAAh+QQJCgAAACwAAAAAEAAQAAADNAi63P5OjCEgG4QMu7DmikRxQlFUYDEZIGBMRVsaqHwctXXf7WEYB4Ag1xjihkMZsiUkKhIAIfkECQoAAAAsAAAAABAAEAAAAzYIujIjK8pByJDMlFYvBoVjHA70GU7xSUJhmKtwHPAKzLO9HMaoKwJZ7Rf8AYPDDzKpZBqfvwQAIfkECQoAAAAsAAAAABAAEAAAAzMIumIlK8oyhpHsnFZfhYumCYUhDAQxRIdhHBGqRoKw0R8DYlJd8z0fMDgsGo/IpHI5TAAAIfkECQoAAAAsAAAAABAAEAAAAzIIunInK0rnZBTwGPNMgQwmdsNgXGJUlIWEuR5oWUIpz8pAEAMe6TwfwyYsGo/IpFKSAAAh+QQJCgAAACwAAAAAEAAQAAADMwi6IMKQORfjdOe82p4wGccc4CEuQradylesojEMBgsUc2G7sDX3lQGBMLAJibufbSlKAAAh+QQJCgAAACwAAAAAEAAQAAADMgi63P7wCRHZnFVdmgHu2nFwlWCI3WGc3TSWhUFGxTAUkGCbtgENBMJAEJsxgMLWzpEAACH5BAkKAAAALAAAAAAQABAAAAMyCLrc/jDKSatlQtScKdceCAjDII7HcQ4EMTCpyrCuUBjCYRgHVtqlAiB1YhiCnlsRkAAAOwAAAAAAAAAAAA==" />
			</div>
		</div>
	</div>
</form>
```
