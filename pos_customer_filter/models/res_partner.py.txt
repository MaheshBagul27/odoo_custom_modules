from odoo import models

class PosSession(models.Model):
    _inherit = 'pos.session'

    def _loader_params_res_partner(self):
        params = super(PosSession, self)._loader_params_res_partner()
        # Only load customers where use_partner_credit_limit is False
        params['domain'] = [('use_partner_credit_limit', '=', False)]
        return params
